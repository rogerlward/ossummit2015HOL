##Admin Exercise 1: Organizations, Spaces, and Domains

Cloud Foundry is a multi-tenent PaaS, allowing multiple users,
applications and organizations to share the PaaS. To enable this Cloud
Foundry defines Organizations (Orgs) and Spaces as ways to partition
the PaaS amongst multiple collaborators and applications.

### Orgs

An organization is a top-level group of users, spaces, and
domains. Each Org is has an associated Quota Plan which limits the
resources available to the Organization.

![orgs](http://www.activestate.com/sites/default/files/blog_import_images/org-with-quota-defs-400px.png)



### Spaces

Orgs contain one or more Spaces, which are used to contain Cloud
Foundry applications. A space provides a set of users access to a
shared location for application development, deployment, and
maintenance. Each space role applies only to a particular space.

Applications and Service Instances are assigned to individual Spaces.

![spaces](http://www.activestate.com/sites/default/files/blog_import_images/spaces-with-apps-services-450px.png)

### Domains


A Cloud Foundry domain is a fully-qualified, second-level or lower
domain name (e.g. "example.com" or "paas.example.com"). Spaces within
an organization inherit all its domains. Applications within these
spaces can use any of these domains to make application routes.

![domains](http://www.activestate.com/sites/default/files/blog_import_images/org-space-route-domain-450px.png)


### Orgs Exercises

List orgs

```
cf orgs
```

Create a new org

```
cf create-org MY-ORG
```

Create a new org

```
cf create-org MY-ORG
```

Delete a org

```
cf delete-org MY-ORG
```


### Spaces Exercises

List current spaces

```
cf spaces
```

Create a new space

```
cf create-space specify-a-space-name-here
```

Observe your space has been created

```
cf spaces
```

Switch to a new space

```
cf switch-space space-name
```




### Domains Exercises

List domains
```
cf domains
```

Create a new domain
```
cf create-domain MY-DOMAIN
```

Create a new domain
```
cf create-domain MY-DOMAIN
```

Delete a domain
```
cf delete-domain MY-DOMAIN
```
