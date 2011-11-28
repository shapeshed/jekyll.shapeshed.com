--- 
layout: post
title: Curving The Edges of Images in Photoshop
excerpt: "I get a lot of search engine referrals from people looking to create curved images or curved rectangles in Photoshop. So here's a quick tutorial to show you how. "
categories: [Design, Photoshop]
---
**UPDATE 15/02/07**: Quite a few people seem to have been having trouble with this so I've added a video at the bottom. There are some good comments below too that should help you if you have difficulties

## Curved rectangles

Curved rectanges are simple - there is tool in photoshop that will create the shape for you. You can access this tool by pressing U. This selects the Custom Shape Tool. To create a curved rectangle you need the Rounded Rectangle Tool, which is the second one down.

![The Curved Rectangle Tool][1] 

Then simply draw your rectangle. You change the amount of curve by altering the radius. In the default workspace this is at the top of your screen. If you don't see your default workspace you can return to this by going to Window > Workspace > Default Workspace

Examples of curved rectangles where the radius alters the curve

![Examples of Curved Rectangles][2] 

## Curving the edges of shapes or photographs

Often you will want to break up the hard edges of photographs of solid shapes like rectangles or photographs. By applying a mask you can do this easily.

When you open your photo the image will have one layer by default. This will be called "Background". In order to create curved edges you will need to copy this layer. Right click on the layer and choose Duplicate layer. Then hide or delete the original Background layer. Hiding is probably preferable incase it all goes wrong! 

### Step one - Draw the Curve

Selected the Rounded Rectangle as we did in the first example. Then draw a rectangle over your shape. You can change the curve you have on your rectangle using the radius option. Don't worry about the colour - you won't see this in the end.

![Drawing the curve][3] 

### Step two - Select the Curved Rectangle

In order to create a mask you need to select the curved rectangle you have just drawn. To do this hover over the preview of the shape in the layers window. In the example this is the red square. Hold down the Apple Key on a Mac (<strike>ALT</strike> CTRL on Windows) and you will see a white rectangle appear next to the hand. Click and the shape will be selected - you will note the familiar black and white edge to the shape showing it is selected. 

![Select the Curved Rectangle][4] 

### Adding a vectorlayer mask

To curve off the shape we use a vectorlayer mask. To create this you now select the Background copy layer. You should see that your curved rectangle is still selected. At the bottom of the layers pane is what looks like a small camera. As you hover over it is says "Add vectorlayer mask". Click this to add the vectorlayer mask. When you add the mask you will see the parts of the picture that are not under the mask disappear.

![Add Layer Mask][5] 

### Showing the finished image

To show the finished image simply turn off the visibility of your curved rectangle layer. You do this by clicking the eye icon in the layers window next to your curved rectangle layer. Then save out your image for the web and your are done!

![The finished curved image][6] 

### Use your imagination

You can use any shape to create a Vector mask so why not explore the elements within the Custom Shapes Tool? You can use any of them to mask off your photograph or shape.

### Still don't get it? Watch the movie!

<video controls>
  <source src="/movies/mp4/curving.mp4" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"' />
  <source src="/movies/ogv/curving.ogv" type='video/ogg; codecs="theora, vorbis"' />
  To view this video you need the latest version of <a href="http://www.apple.com/safari/">Safari</a>, <a href="http://www.mozilla.com/firefox/">Firefox</a> or <a href="http://www.google.com/chrome">Chrome</a>. Alterantively download the videos and watch them offline. <a href="/movies/mp4/curving.mp4">Windows / Mac (mp4)</a>, <a href="/movies/mp4/curving.mp4">Linux (ogv)</a>
</video>


 [1]: /images/articles/rectangle_tool.jpg "The Curved Rectangle Tool"
 [2]: /images/articles/curved_rectangles.png "Examples of Curved Rectangles"
 [3]: /images/articles/draw_curve.jpg "Drawing the curve"
 [4]: /images/articles/select_shape.jpg "Select the Curved Rectangle"
 [5]: /images/articles/add_vector_mask.jpg "Add Layer Mask"
 [6]: /images/articles/final_curved_shape.jpg "The finished curved image"

