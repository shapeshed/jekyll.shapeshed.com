--- 
layout: post
title: Nifty Unix Tools - sort
excerpt: Sort is a great little UNIX tool for sorting text files and streams. Here's a quick overview of how it works.
categories: [Unix]
---

## Sort

To demonstrate some of the features here is an example CSV file with some of my favorite cheeses:

{% highlight bash %}1,Brie de Meaux,1.99
2,Maroilles,1.13
3,Stinking Bishop,1.65
4,Munster,1.29
{% endhighlight %}

The file is sorted by the id number in the first column. Let's say we want to sort this by the name of the cheese.

{% highlight bash %}sort -k2,2 -t , test.csv{% endhighlight %}

The -t flag allows us to specify a delimiter which in this case is the comma character. The -k flag lets us specify a key to sort on. The values are the start and end point for the key. This option says take the second value on the line according to the delimiter. 

This gives us an alphabetically sorted list:

{% highlight bash %}1,Brie de Meaux,1.99
2,Maroilles,1.13
4,Munster,1.29
3,Stinking Bishop,1.65
{% endhighlight %}

Sort also lets us sort numerically so if we wanted to sort on the third price column we can use

{% highlight bash %}sort -n -k3,3 -t , test.csv{% endhighlight %}

Here we use the -n flag which say sort numerically and we have shifted the key to the third column.

{% highlight bash %}1,Brie de Meaux,1.99
3,Stinking Bishop,1.65
4,Munster,1.29
2,Maroilles,1.13

{% endhighlight %}

If we want to sort by the cheapest price we can reverse the sort with the -r flag

{% highlight bash %}sort -r -n -k3,3 -t , test.csv{% endhighlight %}

This gives us the cheapest price first 

{% highlight bash %}2,Maroilles,1.13
4,Munster,1.29
3,Stinking Bishop,1.65
1,Brie de Meaux,1.99
{% endhighlight %}

## Conclusion

The sort tool can sort strings and numbers in text files and streams. By using keys you can narrow down the search criteria and get the information you want quickly. It also has options clean up dirty data, although for anything non-trivial you'll probably want to use something like [sed][3].

It is a great little tool for daily use on in the shell and can make output information much easier to read in shell scripts and standard output. 

## Further reading

* [sort man page][1]
* [Unix sort command][3]

[1]: http://linux.die.net/man/1/sort
[2]: http://linux.die.net/man/1/sed
[3]: http://www.softpanorama.org/Tools/sort.shtml
	
