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
