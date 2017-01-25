#### [Hierarchical Clustering] (http://en.wikipedia.org/wiki/Hierarchical_clustering)


Euclidean distance is what you learned about in high school algebra. Given two points on a plane, (x1,y1) and (x2,y2), the Euclidean
distance is the square root of the sums of the squares of the distances between the two x-coordinates (x1-x2) and the two
y-coordinates (y1-y2). You probably recognize this as an application of the Pythagorean theorem which yields the length of the
 hypotenuse of a right triangle.

 In this case, we can use __Manhattan__ or city block distance (also known as a taxicab metric). This picture, copied from
| http://en.wikipedia.org/wiki/Taxicab_geometry, shows what this means. More formally, Manhattan distance is the sum of the absolute values of the distances between each coordinate, so the distance between the points (x1,y1) and (x2,y2) is |x1-x2|+|y1-y2|. As with Euclidean distance, this too generalizes to more than 2 dimensions.


dist()
plot(as.dendrogram(hc))
 hc < hclust(distxy)
 
__kmeans()__

 There are several ways to do this. We'll just mention two. The first is called complete linkage and it says that if you're trying to measure a
| distance between two clusters, take the greatest distance between the pairs of points in those two clusters. Obviously such pairs contain one point
| from each cluster.

The second way to measure a distance between two clusters that we'll just mention is called average linkage. First you compute an "average" point in
| each cluster (think of it as the cluster's center of gravity). You do this by computing the mean (average) x and y coordinates of the points in the
| cluster.

 We won't say too much on this topic, but a very nice concise tutorial on creating heatmaps in R exists at
| http://sebastianraschka.com/Articles/heatmaps_in_r.html#clustering. Here's an image from the tutorial to start you thinking about the topic. It
| shows a sample heat map with a dendrogram on the left edge mapping the relationship between the rows. The legend at the top shows how colors relate
| to values.

#### K- means Clustering general

 * Partitioning Approach
  * Fix a number of clusters
  * Get "Centroids" of each cluster
  * Assign things to closest centroid
  * Recalculate centroides
 * Requires
  * A defined distance metric
  * A number of clusters
  * An Initital Guess to cluster centroids
 * Produces
  * Final Estimate of cluster Centroids
  * An Asignment of each porint to clusters
  
  ### Principal Component analysis, Singular value Decomposition
  PCA and SVD are used in both the exploratory phase and the more formal modelling stage of analysis. We'll focus on the exploratory phase and briefly touch on some of the underlying theory.
  
   As data scientists, we'd like to find a smaller set of multivariate variables that are uncorrelated AND
| explain as much variance (or variability) of the data as possible. This is a statistical approach.
 In other words, we'd like to find the best matrix created with fewer variables (that is, a lower rank
| matrix) that explains the original data. This is related to data compression.
 Two related solutions to these problems are PCA which stands for Principal Component Analysis and SVD,
| Singular Value Decomposition. This latter simply means that we express a matrix X of observations (rows) and
| variables (columns) as the product of 3 other matrices, i.e., X=UDV^t. This last term (V^t) represents the
| transpose of the matrix V.


svd()

#### Pricipal component analyisis
 Now we'll talk a little about PCA, Principal Component Analysis, "a simple, non-parametric method for
| extracting relevant information from confusing data sets." We're quoting here from a very nice concise paper
| on this subject which can be found at http://arxiv.org/pdf/1404.1100.pdf. The paper by Jonathon Shlens of Google Research is called, A Tutorial on Principal Component Analysis.

| We'll demonstrate this now. First we have to scale mat, our simple example data matrix.  This means that we
| subtract the column mean from every element and divide the result by the column standard deviation. Of
| course R has a command, scale, that does this for you. Run svd on scale of mat.

svd(scale(mat))
prcomp(scale(mat))

| Now you're probably convinced that SVD and PCA are pretty cool and useful as tools for analysis, but one
| problem with them that you should be aware of, is that they cannot deal with MISSING data. Neither of them
| will work if any data in the matrix is missing. (You'll get error messages from R in red if you try.)
| Missing data is not unusual, so luckily we have ways to work around this problem. One we'll just mention is
| called imputing the data.
This uses the k nearest neighbors to calculate a values to use in place of the missing data. You may want to
| specify an integer k which indicates how many neighbors you want to average to create this replacement
| value. The bioconductor package (http://bioconductor.org) has an impute package which you can use to fill in
| missing data. One specific function in it is impute.knn.

| We'll close now with a few comments. First, when reducing dimensions you have to pay attention to the scales
| on which different variables are measured and make sure that all your data is in consistent units. In other
| words, scales of your data matter. Second, principal components and singular values may mix real patterns,
| as we saw in our simple 2-pattern example, so finding and separating out the real patterns require some
| detective work. Let's do a quick review now.
