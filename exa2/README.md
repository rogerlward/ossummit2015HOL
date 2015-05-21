##Admin Exercise 2: Security Groups

Cloud Foundry Security Groups are used to constrain outbound (egress)
network traffic, from the application container to the network.

A security group is essentially a mapping of firewall rules to a
specific space or org, in which case all applications deployed to the
space or org will be constrained by the security group. Security
groups can also be applied to the entire Cloud Foundry instance.

A handful of commands are available to query and manage security
groups.


### Security Group Rules

The egress rules are specified as JSON, and can apply to TCP, UDP, and
ICMP traffic. Port ranges and subnets can be specified.

Here's example security group JSON that allows UDP traffic to 10.0.0.5
to port 80:

```
[{"protocol":"udp","destination":"10.0.0.5","ports":"80"}]
```

Here's a more general example that allows TCP traffic to any port on
any host on the 10.*.*.* network:

```
[{"protocol":"tcp","destination":"10.0.0.0/24","ports":"1-65535"}]
```


### Security Group Commands

Security groups can be created, deleted, queried, and applied to orgs
and spaces. Only admin users can create and manage security groups.

You'll find two example security group files in this directory,
corresponding to the above examples.

First we'll create a new security group based on one of these files:

```
cf create-security-group MYSECURITYGROUPNAME1 --token-file security-group-1
```

Create a second group:

```
cf create-security-group MYSECURITYGROUPNAME2  --token-file security-group-1
```

List security groups:

```
cf security-groups
```


List information about a specific group:

```
cf security-group MYSECURITYGROUPNAME2
```

Bind a security group to a specific org and space:

```
cf bind-security-group --organization user700-org --space user700-space MYSECURITYGROUPNAME2
```

List the information about this security group again:

```
cf security-group MYSECURITYGROUPNAME2
```

Now unbind this security-group from the org and space:

```
cf unbind-security-group --organization user700-org --space user700-space MYSECURITYGROUPNAME2
```

And delete the security group:

```
cf delete-security-group <security_group>
```


### Summary

Security groups are an essential tool to further secure the
applications and users running in the PaaS, allowing the restriction
of outbound network traffic to a limited set of hosts and networks.



