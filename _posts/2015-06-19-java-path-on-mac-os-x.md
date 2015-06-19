---
layout: post
title: "Java PATH on Mac OS X"
description: ""
category: 
tags: [osx] [path] [java] [jdk]
---

Problem: I've just installed new Java JDK from Oracle's site, but OS X terminal is still using the default Java version (that one set in OS X System Preferences).


NOTE: Make sure that you've installed JDK, not JRE !!

There is a quick'n'drity way to make OS X use Java installed from Oracle's .dmg file:
```
sudo unlink /usr/bin/java
sudo ln -s /Library/Java/JavaVirtualMachines/jdk1.7.0_79.jdk/Contents/Home/bin/java /usr/bin
```

{% include JB/setup %}
