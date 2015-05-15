#Cloud Foundry on OpenStack Hands-On Labs

##Exercise 1: Target the Cloud Foundry instance

Make sure you've installed the stackato CLI for accessing the Cloud Foundry instance.

Target the Cloud Foundry instance by substituting the URL with the one provided and use the following command.

```
cf api --skip-ssl-validation https://api.15.125.77.39.xip.io
```

The output should look something like below.

```
Setting api endpoint to https://api.15.125.77.39.xip.io...
OK

                   
API endpoint:   https://api.15.125.77.39.xip.io (API version: 2.8.0)   
Not logged in. Use 'cf login' to log in.
```

You can log in with the following command. Login credentials will be provided.

```
cf login
```

The output will look something line below.

```
API endpoint: https://api.15.125.77.39.xip.io

Username> rags

Password> 
Authenticating...
OK

Targeted org workshop-org

Targeted space workshop-space


                   
API endpoint:   https://api.15.125.77.39.xip.io (API version: 2.8.0)   
User:           rags@acm.org   
Org:            workshop-org   
Space:          workshop-space
```


You can verify that you are targeted and logged in by running with the following command.

```
cf apps
```

and the services that are installed with the following command.

```
cf marketplace
```

You should see an output that lists the different services and the plans that have been pre-installed for your convenience.

```
+------------+------+------------------------------------------+---------+------+--------+----------+---------+--------+------+
| Vendor     | Plan | Description                              | Details | Free | Public | Provider | Version | Broker | Orgs |
+------------+------+------------------------------------------+---------+------+--------+----------+---------+--------+------+
| filesystem | free | Persistent filesystem service            | free    | yes  | yes    | core     | 1.0     |        |      |
| harbor     | free | External port mapping service            | free    | yes  | yes    | core     | 1.0     |        |      |
| memcached  | free | Memcached in-memory object cache service | free    | yes  | yes    | core     | 1.4     |        |      |
| mongodb    | free | MongoDB NoSQL store                      | free    | yes  | yes    | core     | 2.4     |        |      |
| mysql      | free | MySQL database service                   | free    | yes  | yes    | core     | 5.5     |        |      |
| postgresql | free | PostgreSQL database service              | free    | yes  | yes    | core     | 9.1     |        |      |
| rabbitmq   | free | RabbitMQ message queue                   | free    | yes  | yes    | core     | 2.8     |        |      |
| rabbitmq3  | free | RabbitMQ message queue                   | free    | yes  | yes    | core     | 3.1     |        |      |
| redis      | free | Redis key-value store service            | free    | yes  | yes    | core     | 2.8     |        |      |
+------------+------+------------------------------------------+---------+------+--------+----------+---------+--------+------+
```

We will be pushing an app. and connecting to a service in the upcoming exercises.

You can also try additional options for the CLI.







