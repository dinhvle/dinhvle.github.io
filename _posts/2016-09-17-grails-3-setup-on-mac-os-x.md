---
layout: post
title: Grails 3 setup on Mac OS X
---

<amp-img width="800" height="210" layout="responsive" src="/assets/images/grails-logo.png"></amp-img>

I have to install [Grails](https://grails.org/){:target="_blank"} recently to work on one of my project. This is a quick and easy installation guide.

#### Installing JDK

For Grails 3 you will need Java Development Kit (JDK) version 1.7 or above. Although [Java SE Development Kit 7](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html){:target="_blank"} is no longer getting update from Oracle, you should install this kit since a lot of Grails version only work with it. Just download and run installer.

After installation, you can verify by running:

```
java -version
# java version "1.7.*_*"
```

#### Installing Grails

The easiest way to install Grails on OS X is with [SDKMAN!](http://sdkman.io/index.html){:target="_blank"}. Just run:

```
curl -s get.sdkman.io | bash
```

Follow the instructions on-screen to complete installation.
Open terminal and type the command:

```
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

Then install the latest stable Grails:

```
sdk install grails
```

After installation is complete, check version with:

```
grails -version
# Grails version: 3.*.*
```

And that's it. Unless you are working on a project that need an older version of Grails, in that case just install that version and use it by:

```
sdk install grails 2.4.4
sdk use grails 2.4.4
# For example, if you want to use Grails 2.4.4
```
