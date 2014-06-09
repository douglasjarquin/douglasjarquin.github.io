---
layout: post
title: Java and Tomcat on Ubuntu Hardy
date: '2008-08-04T00:00:00-04:00'
tags:
- tutorial
- java
- ubuntu
tumblr_url: http://douglasjarquin.com/post/1273919943/java-and-tomcat-on-ubuntu-hardy
---
I just spent my entire morning trying to figure out how to install Tomcat on one of my servers. I needed it to demo a business intelligence application, and boy oh boy was it a pain. There is a lot of talk out there about this particular install, but nothing specifically for Ubuntu 8.04 Hardy.

What follows is a quick guide on how to setup Java 1.6.0 and Tomcat 5.5 on a “new” Ubuntu 8.04 Hardy Heron server. We will be using apt-get to install everything, since I hate having to remember to update compiled code.

First things first

First make sure Ubuntu is all up to date:

sudo apt-get update && sudo apt-get upgrade


Java

It was a little hidden, but Ubuntu does have a very detailed how-to for installing Java here. Okay, so it is not very detailed at all. I missed it a few times, but the install steps are there.

sudo apt-get install openjdk-6-jre openjdk-6-jdk


OpenJDK is an open-source Java SDK implementation with support for Ubuntu 8.04 Hardy. Tomcat needs both the JRE and the JDK so make sure to install both if you have not already.

Check on Java

Just to make sure we are all good, run this command to verify that Java installed correctly:

java -version


The output should look something like this:

java version "1.6.0"
OpenJDK Runtime Environment (build 1.6.0-b09)
OpenJDK 64-Bit Server VM (build 1.6.0-b09, mixed mode)


Tomcat

Tomcat was the hard part. There really is not much on the topic, since all Java Web developers are moving to Rails ;), but here is what I put together. There is a package available for Tomcat 5.5, and once installed successfully it will be running on port 8180 of your server. Let’s get to it.

sudo apt-get install apache2 tomcat5.5 tomcat5.5-webapps tomcat5.5-admin


Okay, I kind of let you down here, because the install will fail. Bare with me, it is all part of my plan. If you look carefully at the output you will see why Tomcat’s install failed so miserably.

Setting up tomcat5.5 (5.5.25-5ubuntu1) ...
  * no JDK found - please set JAVA_HOME


Don’t you just love helpful error messages. And I welcome you to the part of the installation that took me hours to figure out. What is required for Tomcat to finish its installation is a simple environment variable. A single line of code that will tell Tomcat where to find our Java install. I tried putting this in the /root/.bashrc, .bash_login, .bash_profile, and ~/.bashrc with no success. I kept thinking there was something wrong with my syntax, but nothing worked. Luckily, I ran into this blog post when doing a Google search for the terms “No JDK found”.

As it turns out, Tomcat has its own place to set this environment variable. Jackpot! Oh, this is why we needed to let the install fail, to create this file for us.

sudo nano /etc/default/tomcat5.5


Then look for this line:

#JAVA_HOME=/usr/lib/jvm/java-6-sun


And make it look like this:

JAVA_HOME=/usr/lib/jvm/java-6-openjdk


Check the newly set JAVA_HOME with:

echo $JAVA_HOME


We did two things. First we uncommented the line, so Tomcat can parse the environment variable set here. Next, we corrected the path to our Java installation. You can check the Java path yourself by typing sudo update-alternatives --config java. Running which java or whereis java will only display symlinks.

So now we run our Tomcat installation command again. Run the whole command again just to make sure all of the packages get installed. If they were installed successfully they will be skipped, so no harm can come from doing this.

sudo apt-get install apache2 tomcat5.5 tomcat5.5-webapps tomcat5.5-admin


Java and Tomcat are now successfully installed! Visit http://localhost:8180 to see how all of my hard work has paid off. Just in case, here are a few useful Tomcat commands:

# Check Tomcat''s status
sudo /etc/init.d/tomcat5.5 status

# Start Tomcat
sudo /etc/init.d/tomcat5.5 start

# Stop Tomcat
sudo /etc/init.d/tomcat5.5 stop


References

Setting up Ubuntu by Slicehost
OpenJDK
Java SDK on Feisty
Java SDK on Feisty Part 2
No JDK Found
