# Code Toolkit: Python, Fall 2023
## Week 2 — Class notes

# Reading Discussion

_So what did everyone thing of the reading?_

Marshall McLuhan made some interesting statements huh?

Marshall McLuhan wrote:

_The title "The Medium Is the Massage" is a teaser—a way of getting attention. There's a wonderful sign hanging in a Toronto junkyard which reads, 'Help Beautify Junkyards. Throw Something Lovely Away Today.' This is a very effective way of getting people to notice a lot of things. And so the title is intended to draw attention to the fact that a medium is not something neutral—it does something to people. It takes hold of them. It rubs them off, it massages them and bumps them around, chiropractically, as it were, and the general roughing up that any new society gets from a medium, especially_


More importantly I want you to take away this:

The communication channel used to communicate any message shapes the message itself.  So if you see a instagram ad that ad was manufactured to get _you_ to click it.  That promoted tweet was crafted to get you to pay attention to it.  That TikTok, was engineered to be captivating. Remember that the way a message is communicated influences the design of the message itself.


Continuing Education in Media Studies read [Manufacturing Consent by Edward S. Herman and Noam Chomsky](/pdfs/Manufacturing%20Consent%20%5BThe%20Political%20Economy%20Of%20The%20Mass%20Media%5D.pdf) and write a short essay on the _Propaganda Model_ (this will replace 2 missed coding homeworks)


# Part 2 :: Introductory Beep Boops 

Let's write a simple "program"

```
print('Hello World')
```

## How to make a drawing

There were some things that many of your drawing instructions did that we will see again later:
placeholders: things like "the first square", "the bottom line". 

*In computer programs these are called variables*

repetition: "do this 4 times", "do this until you connect back to the first line". 

*In computer programs these are called loops*

questions or conditions: "if the shape is not closed, keep drawing". 

*In computer programs these are called conditionals* 

groups of commands: "draw another shape like you did in steps 1-4". 

*In computer programs these are called functions and they are a way to make a group of instructions with a name for re-use*

Introducing the Processing Development Environment

So how does all this translate to Processing?

Let's get started by opening up the Processing Development Environment, or PDE, and look around:
* play button
* stop button
* File > Open
* File > Examples
* Modes: Java & Python

In Processing, a program is called a "sketch".

Let's make a very simple example:
```
size(300,300)
stroke(0,0,255)
fill(0,255,0)
rect(50,50,200,200)
```
```Click File > New > Save``` 
This creates a new folder for this sketch. Note the location. It is probably in a folder called Processing in your Document folder Give the sketch a name and click "Save".

## 2D drawing basics (a.k.a 2D primitives)

*The basic commands to draw shapes are called 2D primitives*

In Processing, we mainly draw using coordinates. Keep in mind a grid where the top-left corner is 0,0. The horizontal dimension is always specified first and is referred to as ```x```, and the vertical dimension is always specified second and is referred to as ```y```.

![GRID](images/grid.png)

```x``` increases as you move to the right, and ```y``` increases as you move down.

So in the following example, what are the coordinates of this pixel?

Highlight this text for an answer: ```x=2```, ```y=3```. Remember, we start counting from 0.
What about in this example: what are the coordinates of this pixel?

Please don't actually count all those pixels! Let's just approximate. Maybe, ```x=30``` and ```y=15```? That seems about right.
Computers require us to be precise. But we can comply with that precision while also being loose and approximate in achieving the goals that we're working toward. We can leave space to play, experiment, estimate, and work by trial-and-error.


Let's look at one command in the [reference](https://py.processing.org/reference/): ```rect()```


```rect(x, y, width, height)```
```
fill(255, 0, 255)
rect(0, 0, 512, 512)
```

The numbers in parenthesis are called ```parameters``` and their order is very important. The [reference](https://py.processing.org/reference/) will tell you what the various ```parameters``` do. In this case, the [reference](https://py.processing.org/reference/) explains that the first parameter is the "```x```-coordinate of the rectangle", the second parameter specifies the ```y``` coordinate, the third is the ```width``` of the shape, and the fourth is the ```height```


*Some comments on lecture note format & style*

Throughout all my lecture notes this semester, I will indicate Processing code by highlighting like so:

```rect(250,250,100,50)```

or

```
rect(250,250,100,50)
```

Whenever text is formatted in this way, it is valid Python Processing syntax. You should be able to copy/paste it into your PDE. I will try my best to also use this formatting when specifying code in my emails, but I can't promise total consistency there as that can get quite tedious.


```ellipse(x, y, width, height)```
```
fill(255, 0, 255)
ellipse(0, 0, 512, 512)
```

```triangle(x1, y1, x2, y2, x3, y3)```
```
fill(255, 0, 255)
triangle(0, 0, 256, 512, 512, 0)
```

Let's look at this ```fill``` function that we keep calling.  Fill sets the fill color for our shapes.

Color is specified using red, green and blue components, called ```RGB``` color. ```Tools > Color Selector``` gives you a helpful tool for selecting colors.  You can also use hue, saturation and brightness, called ```HSB``` color, if you specify that with the ```colorMode()``` command. Let's modify the above example:

```
size(300,300)
stroke(0,0,255)
fill(150,150,255)
rect(50,50,200,200)
```

```fill(r, g, b)```

```
fill(255, 0, 255)
```

```stroke(r, g, b)```
```
stroke(255, 255, 0)
```

You can always add a fourth argument to any color commands to specify alpha which is a common digital media term that means transparency: how see-through a digital image is.

```
size(300,300)
stroke(0,0,255)
fill(150,150,255,50)
rect(50,50,200,200)```
That might not seem very different but if we add a new shape it should be more apparent:
```
```
size(300,300)
stroke(0,0,255)
fill(150,150,255,50)
rect(50,50,200,200)
ellipse(250,250,50,50)
```
Notice that the overlap is slightly darker.

## Draw Order

Drawing order is also important. Intructions are followed from top down, first things first. Lower commands are run later. This means that later drawn shapes will be drawn as if layerd on top of earlier ones. So it's like making a collage: the things that you place down later will be on top.
Let's add a third shape and remove the transparency to see what I mean:

```
size(300,300)
stroke(0,0,255)
fill(150,150,255,255) # 255 as alpha is equivalent to totally opaque
rect(50,50,200,200)
ellipse(250,250,50,50)
triangle(250,250,250,300,300,250)
```

### Some syntax rules
Parenthesis must always come in pairs, open and closed: ```( )```

Processing will try to help you with text highlighting and helpful error messages. If you are confused, check the [reference](https://py.processing.org/reference/) for relevant examples.
Comments are also an important part of coding. They are how you communicate with others (and with yourself in the future!) about what your code does. There are two ways to add comments in Python:

```
# Using a hashtag symbol creates a single line comment, like this
```
Single-line comments can also start midway through a line

```
rect(10,10,10,10)  # like this
```

```
"""
  Using three quotation marks, you can create a comment for a block of
  text, like this. Use this at the top of your files to include your
  name, date, and what this code is for (such as homework week number
  or project)
"""
```


### Raster images
Raster Images. You don't need to always create drawings in this way. You can also load "raster" images into your sketch, and draw them directly into the window. If you've ever done any HTML, this is similar to the way images are included in web pages.
Go to Sketch > Add File, then browse to the image file you want to add and click "Open" . This adds the image file to your sketch directory but does not actually draw it.
To draw it, use the following code:

```
img = loadImage("YOUR-IMAGE-FILENAME.jpg")
image(img, 0, 0)
```

The 0, 0 specifies the x and y location of where in the window to place the image. If you want to control the size of the image, modify the 2nd line to look like this:

```image(img, 0, 0, 50, 25)```

In this case, the image would be 50 pixels wide and 25 pixels tall.
Those numbers are arbitrary and just as a demonstration. You can change them or experiment as much as you'd like. You can find more information in the [reference](https://py.processing.org/reference/): 

* PImage
* loadImage()
* image()

Drawing like this seems tedious! Why would you ever want to do this?

When you want to create something interactive, ie, something that responds to user input. Or when you want to create something with an inhuman amount of repetition. Or maybe when you want to process a large amount of data.

Really, any time you want to create something dynamic ... 

Tools like Photoshop, Illustrator, and Final Cut are fantastic, but they create fixed, closed works. With programming you can produce a creation and imbue it with life.

Maybe instead of drawing an illustration, you define rules to create that illustration, and you write a computer program to draw it. Then you can introduce variance or randomness into the system and instead of 1 drawing, now you have an entire world of drawings that are all similar but also different.
Some programs are fun or helpful to use, some are tools that allow you to create things. When you are creating the program, you can create tools that allow other people to be creative.
  
# Gut Check 
How are those books coming?


# Home Work
## Explore the Processing Python Examples
## Lewitt Trapezoid
![Homework](images/lewitt-trapezoid.jpeg)
