--- 
layout: post
title: Setting up local websites on Snow Leopard
description: A short tutorial on setting up local websites on Snow Leopard.
categories: [OSX, Apache, PHP]
---
Not keen on the command line? Using something like [MAMP][1] may be a better option for you. I'm using vi to edit the files but feel free to use your text editor of choice (TextMate, emacs etc). 

## Step 1 - Creating your site

On OSX websites are stored in /Users/yourname/Sites so it is a good idea to store your site in there. Let's create a site in there. Note you'll need to change yourname in the example to whatever your name is. 

{% highlight bash %}cd /Users/yourname/Sites 
mkdir mysite.com 
cd mysite.com 
printf "My awesome site" > index.html 
{% endhighlight %} 

Great - we've created our site. Now let's set up Apache.

## Step 2 - Setting up Apache

First we need to allow virtual hosts by uncommenting a line in the Apache config file 

{% highlight bash %}sudo vi +/'# Virtual hosts' /etc/apache2/httpd.conf{% endhighlight %} 

Change 
{% highlight apache %}#Include /private/etc/apache2/extra/httpd-vhosts.conf{% endhighlight %} 

to  

{% highlight apache %}Include /private/etc/apache2/extra/httpd-vhosts.conf{% endhighlight %} 

Save the file and exit

## Step 3 - Adding the virtual host

Now we can add the virtual host 

{% highlight bash %}sudo vi /etc/apache2/extra/httpd-vhosts.conf{% endhighlight %} 

Add the following to the end of the file. Remember to change 'yourname' to whatever your name is and also 'mysite.com' to whatever your site folder name is. ServerName is the name you will use to access the site from a browser so if you want something specific change it.  
{% highlight apache %}<VirtualHost *:80> 
  <Directory /Users/yourname/Sites/mysite.com> 
    Options +FollowSymlinks +SymLinksIfOwnerMatch
    AllowOverride All 
  </Directory> 
  DocumentRoot /Users/yourname/Sites/mysite.com 
  ServerName mysite.local 
</VirtualHost> 
{% endhighlight %} 

## Step 4 - Setting your hosts file

As there is no DNS associated with your site we need to set this. 

{% highlight bash %}sudo vi /etc/hosts{% endhighlight %} 

Add the following. This relates to the ServerName you set in the Step 2 

{% highlight bash %}127.0.0.1 mysite.local{% endhighlight %} 

## Step 4 - Start Apache

Now we just need to start apache 

{% highlight bash %}sudo apachectl start{% endhighlight %} 

If you see  
{% highlight bash %}org.apache.httpd: Already loaded{% endhighlight %} 

Then it is already running so restart it using  

{% highlight bash %}sudo apachectl restart{% endhighlight %} 

Now open a browser and visit "http://mysite.local/" (or whatever ServerName you set). All being well you should see a page displaying "My awesome site"

## Step 5 - Enable PHP

If you need PHP then this needs to be enabled. You can do this using 

{% highlight bash %}sudo vi +/php5_module /etc/apache2/httpd.conf{% endhighlight %} 

Change 

{% highlight bash %}#LoadModule php5_module libexec/apache2/libphp5.so{% endhighlight %} 

to 

{% highlight bash %}LoadModule php5_module libexec/apache2/libphp5.so{% endhighlight %} 

Then save and exit. Finally we need to restart apache: 

{% highlight bash %}sudo apachectl restart{% endhighlight %} 

Now lets see if PHP is running ok: 
{% highlight bash %}cd /Users/yourname/Sites 
cd mysite.com 
printf "<?php phpinfo() ?>" > index.php 
{% endhighlight %} 

Now if you open a browser and visit http://mysite.local/index.php you should see the phpinfo() page. Apache is set to serve index.html before index.php so if you delete the index.html you will also be able to access the phpinfo() page at http://mysite.local.

All done! To add further sites just repeat steps 3, 4 and 5.

 [1]: http://www.mamp.info/en/index.html
