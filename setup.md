# Setting up a development environment

## Virtual Machine

Setting up a development environment is part of being a toolsmith, but tonight we don't want you to waste too much time on configuring all kinds of things. That's why we've made a VM available with all the neccessary dependencies.

1. [Download and install Virtual Box](https://www.virtualbox.org/wiki/Downloads)
2. [Download this virtual machine](https://drive.google.com/open?id=0B0n8qSqjK9ZvSWV5Vk9XSHE0VUE)
3. Import Meetup.ova in Virtual Box \(just double click the .ova file\)
4. Start the VM

## Manual setup

We recommend using the VM to get the most out of the meetup. If you'd rather install the tools yourself, please find the instructions below.

### Cypress.io

Simply [follow the instructions on the Cypress.io website.](https://docs.cypress.io/docs/installing-and-running)

Please note: Windows is currently not supported by Cypress.io, so use the VM in that case.

### Cucumber and Karate

* [JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Maven](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)

### FitNesse with HSAC fixtures

Try it out \(sufficient for this workshop\):

* [JVM 7 or 8](http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html)
* Download and unzip sample standalone.zip from [GitHub](https://github.com/fhoeben/sample-fitnesse-project/releases/tag/test-tooling-0.1)

Full developer mode:

* [JDK 7 or 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
* [Maven](https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html)
* [Follow the HSAC instructions](https://github.com/fhoeben/hsac-fitnesse-fixtures#to-create-your-own-test-project)



