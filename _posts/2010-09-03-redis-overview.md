--- 
layout: post
title: An overview of Redis
description: Redis has moved to a 2.0.0 release and is a serious solution for building high-performance, scalable web applications.
categories: [redis]
---
## A key-value store and more

The 2.0.0 release of Redis is out and offers a super-fast key value store that stores data in-memory. It offers a persistent data store along with support for sets, string values and hashes. Performance wise it is [extremely][1] [fast][7] and offers replication without too much fuss. As a developer it is a joy to use. On OSX you can install it using homebrew:

{% highlight bash %}brew install redis{% endhighlight %}

and then start the server with 

{% highlight bash %}redis-server{% endhighlight %}

Now you can connect to it with a client and start adding and retrieving data with a client

{% highlight bash %}redis-cli{% endhighlight %}

## Basics

Here's a basic example of setting and getting a value 

{% highlight bash %}redis> set favorite_drink gin
OK
redis> get favorite_drink
"gin"{% endhighlight %}

Once you have a value you can get information from Redis as to its type:

{% highlight bash %}redis> type favorite_drink
string{% endhighlight %}

And whether a key exists

{% highlight bash %}redis> exists favorite_drink
(integer) 1{% endhighlight %}

I'll cover more of the excellent features in subsequent posts. 

## Using Ruby and Redis

Redis has wrappers for most lanugages including Ruby, Python and PHP. For Ruby you can install the wrapper with

{% highlight bash %}sudo gem install redis{% endhighlight %}

You can then use it in scripts with

{% highlight ruby %}require 'rubygems'
require 'redis'

redis = Redis.new
redis.set "foo", "bar"{% endhighlight %}

## Great for caches and counters

Redis is great for things like counters. Say for example you want to track the number of times a page has been viewed. This is simple with Redis:

{% highlight ruby %}redis.incr "views"
=> 1
redis.incr "views"
=> 2{% endhighlight %}

For non-persistent data like caching it is a really good solution too. You can even use it as the [cache in Rack applications.][3]

## Further reading

* [Simon Willison's Redis Tutorial][4]
* [Redis: Data Cheeseburgers][5]
* [A collection of Redis use cases][6]
* [Salvatore Sanfilippo's blog (the brains behind Redis)][8]
* [Redis command reference][2]

[1]: http://www.mysqlperformanceblog.com/2009/08/27/looking-at-redis/
[2]: http://code.google.com/p/redis/wiki/CommandReference
[3]: http://github.com/jodosha/redis-store
[4]: http://simonwillison.net/static/2010/redis-tutorial/
[5]: http://robots.thoughtbot.com/post/443934722/redis-data-cheeseburgers
[6]: http://www.paperplanes.de/2010/2/16/a_collection_of_redis_use_cases.html
[7]: http://blog.superfeedr.com/redis/mysql/memcache/datastore/performance/redis-at-superfeedr/
[8]: http://antirez.com/
