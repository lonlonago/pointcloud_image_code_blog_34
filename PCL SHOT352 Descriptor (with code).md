#  First, the principle of the algorithm 

##  1. Overview of the principle 

 pcl::SHOT352 Struct Reference 

##  2. Specific process 

    The basic idea of a feature descriptor is to establish a local coordinate system based on neighborhood points, divide the point neighborhood space into several subspaces, and then encode the normal feature statistics of each point in the subspace into a histogram, and then combine the histograms of each subspace to obtain a three-dimensional descriptor. (1) For each query point in the point cloud, construct a covariance matrix of the point neighborhood, which represents the neighborhood radius, represents each point in the neighborhood, represents the centroid of all points in the neighborhood, and represents the distance from the point in the neighborhood to the centroid. (2) By solving the covariance matrix for the available characteristic values and the eigenvectors corresponding to the eigenvalues, the eigenvalues can be obtained in order from large to small, and the corresponding eigenvectors represent 3 coordinate axes respectively. (3) With the query point as the center, a spherical neighborhood with a radius of is established, and the spherical shape is divided into 8, 2, and 2 parts according to the warp, weft, and radial directions, respectively, forming 32 subspaces, as shown in Figure 1. 

 ![avatar]( 20210529181916943.png) 

 ![avatar]( 2021052918203963.png) 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574124716
  ```  
