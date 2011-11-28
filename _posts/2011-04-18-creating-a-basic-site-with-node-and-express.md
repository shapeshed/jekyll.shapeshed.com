--- 
layout: post
title: Creating a basic site with node.js and Express
excerpt: A walkthrough on how to create and deploy a basic site with node.js and the Express framework
categories: [node.js, JavaScript]
---

## What we are going to do

This walkthrough will go over setting up a basic site using [node.js][4] and Express. The walkthrough is aimed at beginners exploring node.js as I've had many questions from friends and colleagues about creating and deploying node apps. If you are not a beginner the article probably won't be of much use to you. We are going to use [express][1], an excellent web framework for node created by [TJ Holowaychuk][2] who seems to be pumping out node.js libraries like he was ten men.

Here is [the site][17] we are going to create. You might also want to grab the [source code][18].

[![Example Express website][31]][17]

## Setup

First we need to setup our development environment. If you are on OSX I've [covered how to setup node.js and npm on OSX][5] in a previous article. If you haven't got everything installed follow that article. 

If you are on Linux there are plenty of [articles on Google][6].

For Windows users there are also [resources on Google][7] but it is a bit more tricky.

## Prerequisites

If everything has installed ok you should now have node.js and npm running on your machine. At the terminal type `node -v` and `npm -v` and you should see something like:

{% highlight bash %}[george@auster ~]$ node -v
v0.4.5
[george@auster ~]$ npm -v
1.0.1rc7{% endhighlight %}

You'll see I'm using the RC of version 1 of npm. I encourage you to install this as this will soon become the default.

## Create an Express site

Still with me? We've covered a lot already! Now let's create an Express site.

First let's create a folder for our project and install Express. 

{% highlight bash %}[george@auster ~]$ mkdir express_example
[george@auster ~]$ cd express_example
[george@auster express_example]$ npm install express{% endhighlight %}

This installs Express into the directory we created. Now we can create the skeleton site. We are going to use [jade][19] and [stylus][20] for templating and css. More on those later.

{% highlight bash %}[george@auster express_example]$ ./node_modules/express/bin/express -t jade -c stylus
destination is not empty, continue? y
   create : .
   create : ./app.js
   create : ./public/stylesheets
   create : ./public/stylesheets/style.styl
   create : ./public/images
   create : ./public/javascripts
   create : ./logs
   create : ./pids
   create : ./test
   create : ./test/app.test.js
   create : ./views
   create : ./views/layout.jade
   create : ./views/index.jade
   - make sure you have installed stylus: $ npm install stylus
   - make sure you have installed jade: $ npm install jade
{% endhighlight %}

You'll see that we need to install a couple of dependencies for stylus and jade support so let's do that. 

{% highlight bash %}[george@auster express_example]$ npm install stylus jade{% endhighlight %}

## Boot the app

That's all the setup you need. Phew. Now you can boot the app:

{% highlight bash %}[george@auster express_example]$ node app.js{% endhighlight %}

You should see `Express server listening on port 3000` and if you open http://0.0.0.0:3000 you'll see the default Express page.

## Using Git

[Git][8] is a version control system that is used heavily in the node.js ecosystem, particulary with [Github][9]. If you aren't familiar with Git [Scott Chacon][12] is your go-to man. He's written extensively and eloquently on Git for beginners and experts. Checkout [Gitcasts][10] for if you are a beginner and [ProGit][11] for more advanced stuff. We are going to use git to version our site and publish it so let's set up our repo now. If your Express server is still running hit CTRL + C to stop it. 

{% highlight bash %}[george@auster express_example]$ git init
[george@auster express_example]$ git add .
[george@auster express_example]$ git commit -m 'initial commit'
{% endhighlight %}

## Developing node.js sites

Normally when you develop a node.js site you'll need ot restart your application each time you make a change. Thankfully our home-grown British JavaScript genius [Remy Sharp][24] has solved this problem with [nodemon][25]. Nodemon will reload your application each time it changes so you don't need to restart it. If you have used [Shotgun][26] for Ruby with [Sinatra][36] it is similar to that. To install run

{% highlight bash %}npm install -g nodemon{% endhighlight %}

Then you can start your app with 

{% highlight bash %}nodemon app.js{% endhighlight %}

Using nodemon means you don't have to restart your app each time you make a change. For more infomation on nodemon see the [README][27]

## HTML in Express

Express is agnostic as to which templating language you use. Templating languages can be a hot topic of debate but for this article I'm going to use [jade][19]. If you've used [haml][28] it is similar to that. In the example we use jade to setup a layout template.


{% highlight jade %}!!! 5
html
  head
    title= title
    link(rel='stylesheet', href='/stylesheets/style.css')
    link(rel='stylesheet', href='/stylesheets/chunkfive-fontface.css')
  body
    header
      nav
        ul
          li 
            a(href="/") Home
          li 
            a(href="/about") About
          li 
            a(href="/contact") Contact
    section#wrapper!= body
        footer 
          section.css-table
            section.four-column
              section.cell
                p Mauris porttitor <br />felis eu leo aliquet<br /> ac rutrum odio aliquet
              section.cell
                p Mauris porttitor <br />felis eu leo aliquet<br /> ac rutrum odio aliquet
              section.cell
                p Mauris porttitor <br />felis eu leo aliquet<br /> ac rutrum odio aliquet
              section.cell
                p Mauris porttitor <br />felis eu leo aliquet<br /> ac rutrum odio aliquet
{% endhighlight %}

This is a common template we can reuse. The line `section#wrapper!= body` pulls in content from the page it is used on. Express also supports variables that you pass through to the template. In this case we pass the title variable. If you are coming from Sinatra this will all be familiar to you. If you are not I recommend consulting the [Express documentation][29].

## CSS in Express

Again Express is agnostic to what you use to generate your CSS - you can use vanilla CSS but for this example I'm using [Stylus][20]. This is very similar to [Sass][30] and supports variables, mixins, functions and more. I really like it! Here's an example from our stylesheet

{% highlight bash %}
/* Set up document
-----------------------------------------------------------------------------*/
body
  font 62.5%/1.5  Helvetica, Arial, "Lucida Grande", "Lucida Sans", Tahoma, Verdana, sans-serif
  text-align center
  background #000

#wrapper
  width 920px
  text-align left 
  margin-left auto 
  margin-right auto
  background #fff
  padding 20px
  border-bottom-radius(15px)
{% endhighlight %}

You'll see that stylus is very terse - you don't need brackets or commas.

## Routing in Express

Routing is similar to [Sinatra][36], allowing you to set up RESTful routes. 

In this example we setup three routes in [app.js][38]

{% highlight javascript %}app.get('/', function(req, res){
  res.render('index', {
    title: 'Home'
  });
});

app.get('/about', function(req, res){
  res.render('about', {
    title: 'About'
  });
});

app.get('/contact', function(req, res){
  res.render('contact', {
    title: 'Contact'
  });
});
{% endhighlight %}

See the [Express documentation][37] for more.

## Publishing your site

We've now developed a basic node.js site using express and we want to host it somewhere. 

There are a number of hosting options for node. It isn't so difficult to host it yourself but for me the easiest and best is [Nodester][13]. If you have used [Heroku][14] the deployment process is very similar. You'll need to request an invite for Nodester (it won't come through immediately though).

{% highlight bash %}curl -X POST -d "email=your_address@gmail.com" http://nodester.com/coupon{% endhighlight %}

[Chris Matthieu][15] has created a [handy video][16] going over how to deploy to Nodester so go and watch that if you don't fancy reading the [documentation][21]. 

Let's create the site on nodester

{% highlight bash %}[george@auster express_example]$ nodester app create express_example app.js{% endhighlight %}

Now we can get the information on the site 

{% highlight bash %}[george@auster express_example]$ nodester app info express_example
nodester info Gathering information about: express_example
nodester warn express_example on port 9451 running: false (pid: unknown)
nodester info gitrepo: ec2-user@nodester.com:/node/hosted_apps/shapeshed/1298-ec0117a54b696d7a9781c79e5283692e.git
nodester info appfile: app.js
{% endhighlight %}

To publish the site we need to add the git repo as a remote our git repo

{% highlight bash %}[george@auster express_example]$ git remote add nodester ec2-user@nodester.com:/node/hosted_apps/shapeshed/1298-ec0117a54b696d7a9781c79e5283692e.git
{% endhighlight %}

And finally we can publish the site by pushing

{% highlight bash %}[george@auster express_example]$ git push nodester master{% endhighlight %}

Nodester will let you know about the deploy - if the deploy was successful you can see your app at http://\[your\_app\_name\].nodester.com/. In this example you can see the site at [http://express\_example.nodester.com][17]

Some other node.js hosting providers include [nodejitsu][32], [Joyent][33], [Cloud Foundry][34] and [Duostack][35].

## Conclusion

This article has showed how to create a very basic site using node.js and Express. It has introduced a number of things from the node.js ecosystem and showed you how to deploy your app to Nodester.

The strengths of node.js as a technology are not so much in building static websites like this. I encourage you to explore some of the node.js libraries to see what it can do. Particularly for real-time applications node.js is extremely exciting and I think we'll see some great apps built on node.js. Try starting with [socket.io][22] for a taste of what to expect.

If you find any inaccuracies in the post [send me an email][23] and I'll update the post.

## Further reading

* [node.js][4]
* [express - node web framework][1]
* [npm - node package manager][3]
* [jade - node.js templating language][19]
* [stylus - node.js css framework][20]
* [Setting up node.js and npm on Mac OSX][5]
* [Nodester - Open Source Hosting for node.js][13]
* [Source code for this article][18]

[1]: http://expressjs.com/
[2]: http://tjholowaychuk.com/
[3]: http://npmjs.org/
[4]: http://nodejs.org/
[5]: http://shapeshed.com/journal/setting-up-nodejs-and-npm-on-mac-osx/
[6]: http://www.google.com/search?q=install+node.js+linux
[7]: http://www.google.com/search?q=install+node.js+windows
[8]: http://git-scm.com/
[9]: https://github.com/
[10]: http://gitcasts.com/
[11]: http://progit.org/
[12]: http://scottchacon.com/
[13]: http://nodester.com/
[14]: http://www.heroku.com/
[15]: http://chrismatthieu.com/
[16]: http://www.youtube.com/watch?v=IMCXbrI_Ygk
[17]: http://express_example.nodester.com
[18]: https://github.com/shapeshed/express_example	
[19]: http://jade-lang.com/
[20]: http://learnboost.github.com/stylus/
[21]: http://nodester.com/api.html
[22]: http://socket.io/
[23]: http://shapeshed.com/contact/
[24]: http://remysharp.com/
[25]: https://github.com/remy/nodemon
[26]: https://github.com/rtomayko/shotgun
[27]: https://github.com/remy/nodemon/blob/master/README.md
[28]: http://haml-lang.com/
[29]: http://expressjs.com/guide.html
[30]: http://sass-lang.com/
[31]: http://shapeshed.com/images/articles/express_example.jpg
[32]: http://www.nodejitsu.com/
[33]: https://no.de/
[34]: http://www.cloudfoundry.com/
[35]: http://www.duostack.com/
[36]: http://www.sinatrarb.com/
[37]: http://expressjs.com/guide.html#routing
[38]: https://github.com/shapeshed/express_example/blob/master/app.js
