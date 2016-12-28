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
