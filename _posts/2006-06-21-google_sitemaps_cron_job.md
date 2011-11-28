--- 
layout: post
title: Google Sitemaps Cron Job
excerpt: "I've recently set up a cron job to run the <a href=\"http://www.google.com/webmasters/sitemaps/docs/en/sitemap-generator.html\">Google Sitemaps Python Script</a> automatically each day. This automatically notifies Google of any changes to the site. I've found that new pages are being indexed very quickly. "
categories: [SEO, Google]
---
There are plenty of good articles out there about how to use the script provided by Google but I struggled to find information on how to set up the cron job for the task. 

So in case anyone else needs it here's a cron job that works for me on Unix. You need to make sure you specify absolute paths. If you don't have root access then talk to your host but they should tell you where python resides. If you want to find out your document root you can find this in PHP by using the [phpinfo()][1] function. 

This runs the scheduled task of generating a sitemap each day at 6am. 

{% highlight bash %}0 6 * * * /enter/your/path/to/python /enter/your/path/to/sitemap/_gen.py --config=/enter/your/path/to/example/_config.xml
{% endhighlight %}

 [1]: http://uk2.php.net/phpinfo
