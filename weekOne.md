# Week One

## Principles of Analytics Graphics


#### Principles
1. Principle 1: Show Comparisons
  * Evidence for a hypothesis is always relative to another competing hypothesis.
  * Always ask, compared to what?
2. Principle 2: Show causality, mechanism, explanation, systemmic structure
  * What is you causal framework
3. Principle: Show Multivariate data
  * Multicatiate = more than 2 variables
  * The real world is multivariate
  * Need to "escape flatland"
4. Principle 4: Integration of evidence
  * Completly integrate words, numbers, images, diagrams
  * Data graphics should make use of many modes of data presentaion
  * Don´t let the tool drive the analysis
5. Principle 5: Describe and document the evidence with appropriate labels, sacles, sources
  * A data graphic should tell a complete story that is credible
6. Principle 6: Content is king
  * Analytical presentations ultimatly stand or fall depending on the quality, relevance and integrity of their content
  
Reference: Eduard Tufte(2006). Beautiful Evidence, Graphics Press LLC. www.edwardtufte.com

## Exploratory Graphs

#### Why do we use graphs in data analysis:
 * To understand data propierties
 * To find patters
 * To suggest nideling strategies
 * To debug analyses
 * To communicate results
  
#### Charactertics of exploratory graphs
 * They are made quickly
 * A large number are made
 * The goal is for personal understanding
 * Axes/legends are generally cleaned up (later)
 * Color/size are primarly used for information


#### Simple Summaries of Data
One dimesion:

 * Five-Number Summary
 * Boxplots  --- boxplot(df$column, col = "blue") --- abline(h =12)
 * Histograms --- hist(df$column, col = "blue", breaks = 100) ---- rug(df$column) ---- abline(v= median(df$column), col = "magenta" lwd = 4)
 * Density Plot --
 * Barplot --  barplot(table(df$column), col = "wheat", main = "Desctiption title")
 
 #### Simple summaries of data
 
 Two dimensions
  * Multiple/ Overlayed 1-d Plots (Lattice/ggplot2)
  * Scatterplots
  * Smooth Scatterplots
  
  > 2 dimensions
   * Overlayed / multiple 2-D plots; coplots
   * Use Color, size, shape to add dimensions
   * Spinning plots
   * Actual 3-D plots (not that useful)
   
#### Multiple Boxplots
 * Boxplot -- boxplot(drat  ~  cyl, data = cars, col ="red")
 *  boxplot(Ozone ~ Month, airquality, xlab = "Month", ylab = "Ozone (ppq)")

#### Mutiple Histograms
 *  Check
 
#### Scatterplot

 * with(cars, plot(hp, disp, col = gear )); abline(h = 300)
 
 #### Multiple Scatterplot
 
 
 ### Summary
 
  * Exporatory plots are "quick and dirty"
  * Let you summarice the data and highlight broad features
  * Exlore basic questions and hypotheses
  * Suggest modeling strategies for next steps

## Plotting Systems

R has three main plotting systems:

#### Base plotting System
 * "Artist's Pallete" model
 * Start with blank canvas build from there
 * Start with plot function or similar
 * Use annotation functions to add/modify (text, lines, points, axis)

Details

* Convinient, mirrors how we think of building plots and analyzing data
* Can't go back once plot has started (ie, to adjust margins); need to plan in advance
* Difficult to "tranlate" to others once a new plot has been created (no graphical "language")
* Plot is just a series of R commands
* You need to control everything


#### The Lattice system
* Plots are created with a single function call (xyploy, bwplot, etc)
* Most useful for confitioning types of plots: Looking at how y changes with x across levels of z
* Things like margins/spacing set automatically because entire plot is specified at once
* Good for putting many plots on the screen

#### The ggplot2 System

* Splits the difference between base and lattice in a number of ways
* Automatically deals with spacing, text, titles but also allows you to annotate by " adding" to a plot
* Superficial similarity to lattice but generally easier/more intuitive use\
* Default mode makes many choices for you ( but can still customize)


#### Summary
* Base: "artist's pallete" model
* Lattice: Entire plot specified by one fucntion; conditioning
* ggplot2: Mixes elements of Base and Lattice


#### Base Plotting systems in R

The core plotting and grpahical engine in R is encapsulated in the following packages:

* graphics: contaings plotting functions for the "base" graphic systems, including plot, hist, boxplot and many mores
* grDevices: contaings all the code implementing the various graphics devices, including X11, PDF, PostScript, PNG , etc...

The lattice plotting system is implemented using the following packages:

* lattice: contaings code for producting Trellis graphics, which are independent of the "base" graphics system. includes functions like xyplot, bwplot, levelplot
* grid: Implements a different graphing system independent of the "base" system; the lattice package builds on top of grid; we seldom call functions form the rid package directly


#### The process of making a plot\

When making a plot one must first make a few considerations"
 * Where will the plot be made ? On the screen? in a file?
 * How will the plot be used>
  * Is the plot for viewing temporarly on the screen?
  * Will it eventually be presented in a web browser?
  * Will it eventually end up in a paper that might be printed?
  * Are you using it in a presentation?
* Is there a large amount of data going into the plot? 
* Do you need to be able to dynamically resize the graphic?

* what graphic system will you use: base: lattice, or ggplot2?
* Base graphic are usually constructed piecemeal, with each aspect of the plot handled separetely through a series of functions calls; this is often conceptually simpler and allows plotting to mirror the thought process
* Lattice graphics are usually created in a single function call, so all of the graphics parameters have to specified at once, specifying everything everything at once allows R to automatically calculate the necessary spacings and font sizes.
* ggplot2 combines concepts from both base and lattice graphics but uses an independent implemenetation.

We focus on using the base plotting system to create graphics on the screen device.


#### Base graphics

Base graphics are used most commonly and are a very powerful system for creating 2-D graphics

* There are two phases to creating a base plot
  1. Initializing a new plot
  2. Annotating (adding to) an existing plot

* Callling plot(x,y) or hist(x) will launch a graphics device (if one is not already open) and draw a new plot on the device
* If the arguments to plot are not of some special class, then the default method for plot is called; this function has many arguments, letting you set the title, x axis label, y axis label, etc.
* The base graphic system has many parameters that can set and tweaked; these parameters are documented in ?par; it woudn't hurt to try to memorize this help page.

##### Key Base Graphic Parameters

Many base plotting functions share a set of parametes. Here are few key ones:

* pch: the plotting symbol (default is open circle)
* lty: the line type (default is solid line), can be dashed, dotted, etc
* lwd: the line witdh, specified as an interger multiple
* col: the plotting, specified as a number, string, or hex code; the colors() function gives you a vector of colors by name
* xlab: character string for the x-axis label
* ylab: character string on the y-axis label

The par() function is used to specify global graphics parameters that affect all plots in an R session. These parameters can be overridden when specified as arguments to specific plotting functions:

* las: the orientation of the axis labels on the plot
* bg: the background colot
* mar: the margin
* oma: the outer margin size*default is 0 for all sides)
* nfrow: number of plots per row, column ( plots are filled row-wise)
* mfcol: number of plots pero row, column (plots are filled column-wise)

par("lty")


### Base plotting Functions
 * plot: makes a scatterplot, or other type of plot depending on the class of the object being plot
 * lines: add lines to a plot, given a vector x values and a corresponding vector of y values (or a 2-column matrix); this function just connects the dots
 * points: add points to a plot
 * add text to a plot using especified x,y coordinates
 * title: add notations to x, y axis labels, title, subtitle, outer margin
 * mtext: add arbitrary text to the margings (inner, outer) of the plot
 * axis: adding axis ticks/labes
 
 ##### Summary
 * Plots in the base plotting system are created by calling succesive R functions to "build up" a plot
 * Plotting occurs in two stages:
   * Creation of a plot
   * Annotation of a plot (adding lines, points, text, legends)
 * The base plotting system is very flexible and offers a high degree of control over plotting
 
#### Graphics Devices

 * A graphic device is something where you can make a plot appear
  * A window on your computer (screen device)
  * A PDF file (file device)
  * A PNG or JPEG file (file device)
  * A scalable vector graphic (SVG) file (file device)

* When you make a plot in Rm it has to be "sent" to a specific graphic device
* The most common place a plot is to be "sent" is the screen device
 * On Mac the screen device is launched with the quartz()
 * On Windoes the screen device is launched with windows()
 * On Unix/Linux the screen device is launched with x11()
 
 When making a plot, you need to consider how the plot will be used to detemine what device plot should be sent to
  * The list of device is found in ?Devices; there are also devices created by users on CRAN
 
 For quick visualization and exploratoty analyisis, usually you want to use the screen device
  * fucntions like plot in base, xyplot in lattice, or qplot in ggplot2 will default sending a plot to the screen
  * On a given platform (Mac, Windows, Unix/Linux) there is only one screen device
  
 For plots that may be printed out or be incorporated into a document, (e.g. papers/reports, slide presentations), usually a file device is more appropiate
  * The are many different file devices to choose from
  * Not all grpahic devices are available in all platforms


#### How Does a plot Gets Created

There are two basig approaches to plotting, The first is most common (Screen Device):
1. Call a plotting fucntion like plot, xyplot or qpot
2. The plot appears on the screen device
3. Annotate plot if necessary
4. Use

The decond approach to plotting is most commonly used for file devices"
1. Explicitly Launch a grapchics device
2. Call a plotting function to make a plot (Note: if you are using a file device, no plot will appear on the screen)
3. Annote plot if necessary
4. Excplicity close grphic device with dev.off() (this is very important!)

```R
pdf(file = "myplot.pdf")
with(faithdul,plot(eruptions,waiting)
title(main = "Old Faithful Geyser Data")
dev.off()
```

#### Graphic File Devices

There are two basic types of file devices" **vector** and **bitmap** devices

Vector Format
 * pdf: Usefel for line-type graphics, resizes well, ususally portable
 * svg: XML - based scalable vector graphics; supports animation and interactivity, potentially useful for web-based plots
 * win.metafile: Windows metafile format
 * postscript: older format, also resizes wel, usuatlly portable
 
 Bitmap formats:
 
 * PNG: bitmapped format, good for line drawing or images with solid colors, uses lossless compression, most web browsers can read this format natively, good for plotting many many points, does not resize well
 * jpeg: good for fotographs or natural scenes, uses lossy compression, good for plotting many many points, does not resize well, can be read by alsmost any computer and any web broser, not great for line drawing
 * tiff: Creates bitmap files on TIFF format; supports lossless compression
 * BMP: a native Windows bitmapped format (commonly used for icons)
 
 **Multiple Open Graphic Devices**
  * It is possilbe to open multiple graphic devices (screen, file, or both), for example when viewing multiple plots at once
  * Plotting can only occur on one graphics device at a time
  * The currently active graphic device can be found by calling dev.cur()
  * Every open graphic device is assigned an interger ≥ 2.
  * You can change the active grpahics device with dev.set(**interger**) where **interger** is the number associated with the graphics device you want to switch to.
