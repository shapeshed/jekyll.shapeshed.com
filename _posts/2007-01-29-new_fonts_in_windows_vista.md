--- 
layout: post
title: New fonts in Windows Vista
description: A tour of the new fonts in Windows Vista. We can use more fonts!
categories: [Microsoft, Typography]
---
Here they are:

## Calibri

![Calibri][1] 

## Cambria

![Cambria][2] 

## Candara

![Candara][3] 

## Consolas

![Consolas][4] 

## Constantia

![Constantia][5] 

## Corbel

![Corbel][6] 

## Segoe UI

![Segoe UI][7] 

You can degrade your font choice gracefully using CSS so that if a user is on Vista they will get the new font but if they are not they will get another one.

In this example if the user does not have Corbel they get Lucida Sans. If they don't have Lucida Sans they will get Verdana and so on. 

``` css 
font: 62.5%/1.5 "Candara", "Lucida Sans", Verdana, Tahoma, sans-serif;
```

With such a limited choice of system fonts this is something for typography fans to cheer about (well a little bit!).

 [1]: /images/articles/calibri.png "Calibri"
 [2]: /images/articles/cambria.png "Cambria"
 [3]: /images/articles/candara.png "Candara"
 [4]: /images/articles/consolas.png "Consolas"
 [5]: /images/articles/constantia.png "Constantia"
 [6]: /images/articles/corbel.png "Corbel"
 [7]: /images/articles/segoe_ui.png "Segoe UI"
