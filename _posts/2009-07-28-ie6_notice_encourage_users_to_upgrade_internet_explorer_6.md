--- 
layout: post
title: IE6 Notice - Encourage users to upgrade IE6
description: "IE6 is evil and must die so I've created IE6 Notice a 2kb JavaScript file that adds a notice to sites encouraging users to upgrade from IE6. "
categories: [Browsers, Microsoft, Web Standards]
---
## What it is 

IE6 Notice adds a notice for IE6 users encouraging them to upgrade their browser. Users may choose to hide the notice and their preference will be remembered.

<object width="640" height="505"><param name="movie" value="http://www.youtube.com/v/xF2-QbP8Z1k&amp;hl=en&amp;fs=1&amp;hd=1"></param><param name="allowFullScreen" value="true"></param><param name="allowscriptaccess" value="always"></param><embed src="http://www.youtube.com/v/xF2-QbP8Z1k&amp;hl=en&amp;fs=1&amp;hd=1" type="application/x-shockwave-flash" allowscriptaccess="always" allowfullscreen="true" width="640" height="505"></embed></object>

## How to use it 

Adding the notice to your site just requires you to include a single 2kb JavaScript file in your HTML. Copy the following and paste it before the closing body tag of your HTML. If you'd rather not include a remote JavaScript file on your site you can [download the source][1] and host it locally.  

``` html 
<!--[if IE 6]>
<script type="text/javascript" src="http://shapeshed.github.com/ie6-notice/ie6notice-1.0.0.min.js"></script>
<![endif]-->
```

## Find out more

There's a [dedicated page for IE6 Notice][2]. You can also [grab the source][1] from Github - it is licensed under an [Apache License 2.0][3]

 [1]: http://github.com/shapeshed/ie6-notice/
 [2]: http://shapeshed.github.com/ie6-notice/
 [3]: http://www.apache.org/licenses/LICENSE-2.0.html
