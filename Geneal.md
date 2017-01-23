#### [Hierarchical Clustering] (http://en.wikipedia.org/wiki/Hierarchical_clustering)


Euclidean distance is what you learned about in high school algebra. Given two points on a plane, (x1,y1) and (x2,y2), the Euclidean
distance is the square root of the sums of the squares of the distances between the two x-coordinates (x1-x2) and the two
y-coordinates (y1-y2). You probably recognize this as an application of the Pythagorean theorem which yields the length of the
 hypotenuse of a right triangle.

 In this case, we can use __Manhattan__ or city block distance (also known as a taxicab metric). This picture, copied from
| http://en.wikipedia.org/wiki/Taxicab_geometry, shows what this means. More formally, Manhattan distance is the sum of the absolute values of the distances between each coordinate, so the distance between the points (x1,y1) and (x2,y2) is |x1-x2|+|y1-y2|. As with Euclidean distance, this too generalizes to more than 2 dimensions.



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
  
