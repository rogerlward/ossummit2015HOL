#Cloud Foundry on OpenStack Hands-On Labs

##Prerequisites

Needless to say you'll need a laptop! For best experience, a Mac or Linux environment is preferred. In addition we'll need the following software pre-installed.

- [Git](http://git-scm.com/downloads) or "brew install git"	
- [The stackato CLI] (http://www.activestate.com/stackato/download_client) - download the latest version that is appropriate for your laptop and follow the instructions in README.txt.

During the HOL, we will help you with a sandbox environment (the details are below).

However, we want to provide you choices for deployment. We've tested the exercises on multiple instances.

- [https://run.pivotal.io/](https://run.pivotal.io/)
- [https://console.ng.bluemix.net/] (https://console.ng.bluemix.net/)
- [http://www.activestate.com/stackato/sandbox] (http://www.activestate.com/stackato/sandbox)

##Hands-on Labs Cloud Foundry Instance

We will be targeting a Cloud Foundry instance that has been specially provided for the Hands-on Labs.

Create an alias for stackato as cf. You can create an alias for ```stackato``` as ```cf``` in which case the stackato CLI commands will be approximately similar to the cf CLI commands.

The following command worked in my case.

```
alias cf='/Users/srinir16/Downloads/stackato-3.2.1-macosx10.5-i386-x86_64/stackato --skip-ssl-validation'
```

Verify that you're using the right command with any of the following commands.

```
cf --version
```

You should see an output like below.

`stackato 3.2.1 (3.2.1 @ 2015-04-10 14:28:15 -0700)`

or

```
cf --help
```

##Samples and General Directions

Each directory is in a separate sub-directory. ***Ensure that you're in the sub-directory when you're working on a particular exercise and you're issuing the CLI commands from the subdirectory pertaining to the exercise.***

We've also provided a choice of samples. The **instructions will refer to the PCF-demo sample application** but they can be applied to the Node app. or other apps as well.


##Recommended Exercises - User Related

It is recommended that you run through these exercises sequentially since they are progressive with some dependencies. Each exercise should take about 5-10 mins. to complete.

- Exercise 1: [Target the Cloud Foundry Instance](ex1)
- Exercise 2: [Push your application] (ex2)
- Exercise 3: [manifest.yml and more CLI commands] (ex3)
- Exercise 4: [Connect to a service] (ex4)
- Exercise 5: [Scale your application] (ex5)
- Exercise 6: [Health Monitoring] (ex6)
- Exercise 7: [Draining logs] (ex7) 
- Exercise 8: [Blue/Green Deploy] (ex8) [Advanced]

##Recommended Exercises - Admin Related

- Exercise 1: [Orgs, Spaces, Domains] (exa1)
- Exercise 2: [Security Groups] (exa2)

##More Resources

Plenty of samples in multiple languages at [https://github.com/cloudfoundry-samples] (https://github.com/cloudfoundry-samples)

More samples at [https://github.com/Stackato-Apps] (https://github.com/Stackato-Apps)

##Contact

Please contact us on Twitter @ragss or @bcferrycoder.
