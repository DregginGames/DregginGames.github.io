---
layout: post
title: TailTipUI - Building a GUI library!
---

### Why?
So, the biggest question would be WHY, wouldnt it? 
Why create somthing from scratch wich exists in many different form and variations?

The reason is more or less simple: Because i can! The best thing for me to understand something is by doing it. 
How does a GUI work? Well, i didn't know! So lets lern it. 

### Elements
A GUI is a combination of different Elements on the screen wich help the user to interact with the software. 
And since i do OO programming, lets start of with that. A `GeneralElement`! 

From there the structure of my library goes down. There is The Root-Element wich takes care of binding the given Framebuffer. 
Then there is a Text-class wich renders text on the Screen and an Image-class wich renders textures.
Every other type of element (Windows, Buttons, Sliders, ...) can be represented by a group of the above. 
A button is an area wich holds a text and wich reacts to clicks.
A Input-field is just an area wich reads inputs and displays Text on it. And so on.

If you actually take a look at [TailTipUI](https://github.com/mkalte666/TailTipUI) you will also see The different elements.
Or not cause im still working on it ^^

### Rendering
For Rendering there are a few helper funcitons for drawing textured or colored rects and lines. 
I added (or will add) some more stuff to these general functions: Smoothing, radius rendering and Borders.

The easyest might be the smoothing: smoothstep the color with the smoothing-parameter s being the distance from the edge where the function begins.

Then there is the radius rendering. To do that i use these two things:
  
  * Radius Parameter b: the distance from the edges that make the square wich is used for the radius-calculation
  * Radius r: the normalized max-distance from the inner-edge of the square defined with b. Setting this to 0 actually cuts out squares on the edges! 

To draw, it then looks if the pixel is in the square defined with b, and if yes, it looks if the distance to the inner edge is greater then the radius.
Draw not if it is. Also it smoothes out edges, too. 

The last thing would be the border, wich is not implemented yet. Its also more or less easy. If im out of the radius-drawing-area, just find out the distance to the current edge and if its smaller then x overlay the borders color.
If were inside the radius-boxes, do the same but use the distance to the inner edge as reference.

### XML
Well, theres not much to say here. I have written and XML library in C++ called [HoardXML](https://github.com/mkalte666/HoardXML) wich takes the XML loading away from TailTipUI.
Then I parse through the elements and see if i know what the tags name is. I wrote some macro-magic that does the parsing of the tag-tree for me, wich i dont want to talk about (I still have nightmares...).

Elements wich are sub-classes in the DOM tree of the Document assinged as childs to the parent element. Thats where relative positions actually start to make sense!

### End
So here you have some thoughts/ideas/whatever how my GUI lib works.

If you have questions feel free to ask me. Or something. 

Malte

Links:
[HoardXML](https://github.com/mkalte666/HoardXML)
[TailTipUI](https://github.com/mkalte666/TailTipUI)
