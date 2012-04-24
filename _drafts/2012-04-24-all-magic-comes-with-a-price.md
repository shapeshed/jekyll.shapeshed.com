--- 
layout: post
title: All magic comes with a price
description: Leaning on abstractions is powerful but you should know what it means
categories: 
- Opinion
- Node.js
- Rails
---

## Sunday night viewing

I've been watching [Once Upon A Time][6]. It is a new take on traditional Fairy Tales where characters are stuck between The Enchanted Forest and Storybrook and all kinds of temporal mayhem. I pay attention when [Robert Carlyle][5] is on the screen. He brilliantly plays Rumpelstiltskin, a character that loves making deals and issuing a sage catchphrase.

{% blockquote Rumpelstiltkin , Once Upon a Time %}
All magic comes with a price
{% endblockquote %}

Now I think of his face when ever I think of Rails and using any third-party Node.js modules in my apps. Think of this post as therapy. 

## The Rails Generation

It would be fair to say that I am one of the Rails generation. I started developing HTML and CSS, got into JavaScript, then PHP, then Rails. Rails allowed me to create complex applications with very few skills. It was amazing! I was really happy that people who were much smarter than me were giving me a curated toolkit to allow me to make a living creating web applications. I created a couple of applications with Rails 1 but the bulk of my work in Rails is in Rails 2 and Rails 3. 

Rails gives you a huge amount not just in the choices that it makes for you as a developer but also in the ecosystem of gems. Need geolocation? There's a gem for that. Need authentication? There's a gem for that. If fact this is so much the case that when feature requests were received from clients project managers would say "there's probably a gem for that isn't there?". The more experienced I became as a developer the more this approach troubled me. What Rails gave developers was amazing but it promoted a culture of magpie development, namely grabbing the latest shiny gem and using it in your app. A developers profession became as much about knowing what the latest greatest gems were and how to glue them togther using Rails. Behind all of the generators and magic there is a big problem. The vast majority of developers using Rails have no idea what is going on. Because of the quality of Rails and gems writing software could become just a matter of listening to a few podcasts to stay on top of gem releases and filing tickets on open source projects or Stack Overflow when your code doesn't work.

## Abstraction leads to obscurity

At RailsConf 2011 Aaron Patterson gave a talk called "Double Dream Hands: So Intense". Aaron is smart and amongst the hilarity he noted that Rails 3 is slower and more abstracted than ever. If you watch his talk from about [32 minutes][1] he shows the current Middleware stack in Rails. Here is the slide:

I salute him for going through that and understanding how it works. 

{% blockquote Aaron Patterson , Double Dream Hands: So Intense http://www.youtube.com/watch?feature=player_detailpage&v=kWOAHIpmLAI#t=2050s YouTube %}
Rails is getting slower and Rails is getting slower because it is doing more work. 
{% endblockquote %}

He was making a serious point. The more we ask a framework to do the more complex it becomes to maintain and understand. At the point at which he gave the speech abstracting as a discipline made Rails more difficult to understand and slower. 

## UNIX v Rails

Given that most of the Rails community use Macs it seems strange that the Rails framework got to this. The UNIX philosophy is do one thing and do it well. Rails' philoshopy was do everything, make curated decisions and do it well. Judging by the number of successful start-ups created with Rails it did a pretty good job. 

Recently though the Rails core have started to respond to criticisms that there is too much in the core and decisions have been to curate what goes in more strongly. This was the case when support for API apps [was reverted][3] and moved to [a plugin][4]. For Ruby itself there [have been suggestions][5] that the entire standard library itself might be moved out to gems (this is aleady the case with minitest and json). Understanding the Rails codebase remains very difficult, especially for newcomers. 

## History repeating?

Many developers in the Node.js community come from Rails and Ruby and rage against monolithic web frameworks like Rails. It is perhaps why there is no Rails for Node.js. But all developers like abstraction and there are many excellent modules available for developers to use in much the same way as gems in Rails. These modules are less mature and less numerous but there are well established modules that many developers choose over the standard libraries. Take [request][7] for example. It is an excellent, mature module for providing a cleaner api for dealing with HTTP in Node.js. By using it you potentially never need to understand how Node.js handles HTTP requests. Mostly that's a good thing but it is a slippery slope to becoming a magpie developer, grabbing shiny modules and not learning a thing. 

There are increasing pressures within the Node.js community to abstract more, provide generators and make it easier for developers to use. My attraction to Node.js, as much as what it offers, is that when a request comes in and a response goes out I can understand what it happening. We should work hard to keep this the case in the community. There are more and more frameworks being created that abstract having to understand what Node.js is doing. This is of course inevitable as the community matures but there is a real danger that Node.js will suffer the same fate as Rails. 

Keeping things small, understandable and distinct is my biggest hope for what the Node.js community will create. Then I might just be able to get this stupid catchphrase out of my head. 

[1]: http://www.youtube.com/watch?feature=player_detailpage&v=kWOAHIpmLAI#t=1913s
[2]: http://blog.wyeworks.com/2012/4/20/rails-for-api-applications-rails-api-released
[3]: https://github.com/rails/rails/commit/6db930cb5bbff9ad824590b5844e04768de240b1
[4]: http://blog.wyeworks.com/2012/4/20/rails-for-api-applications-rails-api-released
[5]: http://www.imdb.com/name/nm0001015/
[6]: http://beta.abc.go.com/shows/once-upon-a-time
[7]: https://github.com/mikeal/request
