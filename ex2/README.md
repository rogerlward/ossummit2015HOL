#Cloud Foundry on OpenStack Hands-On Labs

##Exercise 2: Push your application

We will use the Pivotal Cloud Foundry field engineering [demo.](https://github.com/Pivotal-Field-Engineering/PCF-demo) that is also [locally available](../samples/PCF-demo). For your convenience, symbolic links are provided. However, you can use the [samples directory](../samples/PCF-demo) to do the same.

Push the application with the following command. The `-n` options picks the defaults. You can try without the `-n` option and pick the defaults otherwise.

```
cf push -n
```

You should see at output something like below.

```
Using manifest file "manifest.yml"
Updating application 'pcfdemo'...
Instances:         1
Application Url:   http://pcfdemo-58e80.15.125.77.39.xip.io
Comparing Application [pcfdemo] to [https://api.15.125.77.39.xip.io -> workshop-org -> workshop-space -> pcfdemo] ... 
  Preserving Environment Variable [JAVA_OPTS]
  Unmap http://pcfdemo-62c69.15.125.77.39.xip.io ... (Change Ignored)
  Map http://pcfdemo-58e80.15.125.77.39.xip.io ... (Change Ignored)
If needed use option --reset to apply the ignored local changes.
Uploading Application [pcfdemo] ... 
  From path /Users/srinir16/emc/src/ossummit/ossummit2015HOL/samples/PCF-demo/target/pcfdemo.war
  Exploding file
  Checking for available resources ...  OK
  Processing resources ... OK
  Packing application ... OK
  Uploading (3K) ... 100% (13943/13943) OK
Push Status: OK
http://pcfdemo-62c69.15.125.77.39.xip.io/ deployed, using a zero-downtime switchover
```

Your application has now been deployed. You can verify that by running the following command.

```
cf apps
```

Which should produce an output that looks something like below.

```
+------------------+---+-----+---------+---------------------------------------------------+----------------+
| Application      | # | Mem | Health  | URLs                                              | Services       |
+------------------+---+-----+---------+---------------------------------------------------+----------------+
| pcfdemo          | 1 | 512 | RUNNING | http://pcfdemo-62c69.15.125.77.39.xip.io          |                |
+------------------+---+-----+---------+---------------------------------------------------+----------------+
```

If you browse the URL provided you should be able to see a heat map that is not yet active since we've not connected to a service. You will also notice a message "No RabbitMQ service bound - streaming is not active" indicating that the RabbitMQ service is not hooked up the application, yet.

We will connect to a service, subsequently.






