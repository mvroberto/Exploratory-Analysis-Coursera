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
  
