--- 
layout: post
title: Auto update an Ubuntu Server with Aptitude
excerpt: How to keep software up-to-date automatically on Ubuntu Server using Aptitude
categories: [Ubuntu, Linux]
---
## Usual disclaimer

This article is provided as it and no responsibility will be taken for things going wrong. Tested on Ubuntu 8.10 server.

## Using Aptitude

If you've ever tried out Ubuntu you'll probably know what aptitude is and how to manage packages. Updating your system is as simple as 
{% highlight bash %}sudo aptitude udpate && sudo aptitude upgrade{% endhighlight %} 

This updates the package lists and presents any upgrades.

## Automating the process

Wouldn't it be easier if you could automate this and forget about it? That way your server can stay up to date without you ever having to worry about it.</p>Create a file called autoupdate.sh and put the following into it:</p> 
{% highlight bash %}#!/bin/bash

# A script to run Aptitude and install any upgrades automatically. 
# Add this to /etc/cron.daily to run the script every 24 hours. 

# This prevents "TERM is not set, so the dialog frontend is not usable." error
PATH="$PATH:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin"

aptitude update
aptitude safe-upgrade -y
aptitude autoclean
{% endhighlight %} 

To run this script daily move it to /etc/cron.daily (making sure it is executable). 

{% highlight bash %}chmod +x autoupdate.sh
sudo chown root:root autoupdate.sh
sudo mv autoupdate /etc/cron.daily 
{% endhighlight %} 

The update will run automatically once a day ensuring you stay up-to-date. 

## Checking logs

You can keep a check on packages that have been installed and removed via the log file that Aptitude generates. 

{% highlight bash %}sudo tail -n 30 /var/log/aptitude{% endhighlight %} 

If you want to check that an upgrade has been applied you can search for it like this 

{% highlight bash %}sudo cat /var/log/aptitude | grep -A 20 -B 20 php5{% endhighlight %} 

Or you can check the currently installed version using (this example is php5) 

{% highlight bash %}aptitude show php5{% endhighlight %}
