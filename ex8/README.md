#Cloud Foundry on OpenStack Hands-On Labs

##Exercise 8: Blue Green Deployments

We will make a simple change to an application, push it. 

Call this, the Green deployment. Once we're happy with the Green deployment, we switchover the original route to this new route so that the netwrok traffic is routed to the new application. If we need to rollback to the original Blue Deployment we can do that as well.

Let's push the application.

Ensure that you're in the subdirectory ex8.

The `manifest.yml` file looks like below.

```
---
applications:
- name: pcfdemo-green
  memory: 512M 
  instances: 1
  services: [rabbitmq]
  host: pcfdemo-a64c4
  path: ./target/pcfdemo-green.war
  env:
   JAVA_OPTS: -Djava.security.egd=file:///dev/urandom
```
Pushing this will deploy the Green deployment with the following command

```
cf push -n
```

The Green Deployment has a changed Copyright from 2014 to 2014-2015 and clicking a state on the map will change it's color to Green (got it :-)?)

Once you're happy with the Green deployment, we will switchover from the original (Blue) deployment to the Green deployment.

Run the following command

```
cf routes
```

Which should yield an output like below.

```
cf routes
```

```
Routes: https://api.15.126.133.139.xip.io -> workshop -> workshop
+----------------------------------------------+--------------------+-----------------+
| Url                                          | Space              | Applications    |
+----------------------------------------------+--------------------+-----------------+
| http://bottle-currency.15.126.133.139.xip.io | workshop::workshop | bottle-currency |
| http://pcfdemo-613d1.15.126.133.139.xip.io   | workshop::workshop | pcfdemo-green   |
| http://pcfdemo-a64c4.15.126.133.139.xip.io   | workshop::workshop | pcfdemo         |
+----------------------------------------------+--------------------+-----------------+
```

We will traverse to the sub-directory ex3 and make a change to `manifest.yml` as below, noting that we switched to a backup route.

```
---
applications:
- name: pcfdemo
  memory: 512M 
  instances: 1
  host: pcfdemo-rags-old
  path: ./target/pcfdemo.war
  env:
   JAVA_OPTS: -Djava.security.egd=file:///dev/urandom
```

push the application with the following command.


```
cf push -n --reset
```

and you should see an output (partial output shown) that looks like below.

```
  Unmap http://pcfdemo-a64c4.15.126.133.139.xip.io ... OK
  Map http://pcfdemo-rags-old.15.126.133.139.xip.io ... OK
```

Back to the ex8 subdirectory.

We modify the `manifest.yml` directory to update the Green deployment to the original route as below.

```
---
applications:
- name: pcfdemo-green
  memory: 512M 
  instances: 1
  services: [rabbitmq]
  host: pcfdemo-a64c4
  path: ./target/pcfdemo-green.war
  env:
   JAVA_OPTS: -Djava.security.egd=file:///dev/urandom
```

We push it as before.


```
cf push -n --reset
```

Now, the Green deployment has been switched over  which can be verified as below

```
cf apps
```

Which should yield an output like below.

```
+-----------------+---+-----+---------+-----------------------------------------------+--------------------+
| Application     | # | Mem | Health  | URLs                                          | Services           |
+-----------------+---+-----+---------+-----------------------------------------------+--------------------+
| bottle-currency | 5 | 128 | RUNNING | http://bottle-currency.15.126.133.139.xip.io  | bottle-currency-db |
| pcfdemo         | 1 | 512 | RUNNING | http://pcfdemo-rags-old.15.126.133.139.xip.io | rabbitmq           |
| pcfdemo-green   | 1 | 512 | RUNNING | http://pcfdemo-a64c4.15.126.133.139.xip.io    | rabbitmq-rags      |
+-----------------+---+-----+---------+-----------------------------------------------+--------------------+
```

we just accomplished the Blue/Green deployment.

