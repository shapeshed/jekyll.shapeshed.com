--- 
layout: post
title: Batch resizing in Photoshop
excerpt: If you have lots of images you want to resize Photoshop can take care of it for you. Using Actions and Automate you can do it once then put your feet up. Here's how it works.
categories: [Design, Photoshop]
---
## The scenario

Let's say for example we have taken some photos for a client and processed them into .tif images. We want to send the client a quick proof, but the images are over 20MB, so too big to send over email. We need to reduce the size of the images. Let's get started by opening one of the larger images. 

## Record the action

With one of our images open we head to the Actions palette. You can get to this via Window > Actions. We want to create a new action. Give your action a name and then hit ok. You will see the red record button is now on, meaning that anything you do in Photoshop now will be recorded.

![Create New Photoshop Action][1] 

Resize the image by heading to Image > Image Size. I'm resizing my image to a width of 600 pixels wide. Then Save the Image for the Web by going to File > Save for Web and Devices. Choose a different folder to save the optimised file into than your originals. When saved close the original image and then click Stop on your action.

![Stop Action][2] 

## Automate it

Now you have your action we can use it to automate an entire folder of image. To do this go to File > Automate > Batch.

![Automate menu in Photoshop][3] 

On the options you want to select your Action under Play - Action (pick the one you have just created). Then under Source choose Folder and then select your Source folder. Then you should be all set. Click OK and it will start to run through each of the images in your folder! Magic.

## Watch the video

If you feel you've missed something watch the video. If you'd like the HD version you'll have to [watch it on Vimeo.][4]

<object width="400" height="300">	
<param name="allowfullscreen" value="true" />	
<param name="allowscriptaccess" value="always" />	
<param name="movie"
value="http://www.vimeo.com/moogaloop.swf?clip_id=1050103&amp;server=www.vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" />	
<embed src="http://www.vimeo.com/moogaloop.swf?clip_id=1050103&amp;server=www.vimeo.com&amp;show_title=1&amp;show_byline=1&amp;show_portrait=0&amp;color=&amp;fullscreen=1" type="application/x-shockwave-flash" allowfullscreen="true" allowscriptaccess="always" width="400" height="300"></embed></object><br /><a href="http://www.vimeo.com/1050103?pg=embed&sec=1050103">Batch resizing in Photoshop</a> from <a href="http://www.vimeo.com/user472031?pg=embed&sec=1050103">George Ornbo</a> on <a href="http://vimeo.com?pg=embed&sec=1050103">Vimeo</a>.

 [1]: /images/articles/create_new_action.jpg
 [2]: /images/articles/stop_action.jpg
 [3]: /images/articles/automate_batch.jpg
 [4]: http://www.vimeo.com/1050103


