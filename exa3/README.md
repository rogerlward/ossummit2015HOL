##Admin Exercise 3: Quotas

With a multi-tenant PaaS like Cloud Foundry, it's essential that
per-user and per-app resources be capped. Quota plans are used for this purpose,
and are associated with each org to restrict the  various resources
available to users in the org. The resources that are managed by
quotas include:

* Number of services
* Number of applications
* Memory allocation
* Number of routes
* Sudo privileges


To list the defined quota plans:

```
cf quotas
```

To show the details of a specific quota plan:

```
cf quota show demo
```


To create a new quota plan limiting the number of routes and app instances:

```
cf quota create MYQUOTAPLAN --routes 3 --droplets 5
```

To show the details of a specific quota plan:

```
cf quota show demo
```

To apply a quota to an org:

```
cf quota-org user700-org MYQUOTAPLAN
```


### Summary

Quotas are used to restrict the resources available to users in an
org. Similar concepts (not covered here) apply to managing the quotas
associated with a space.
