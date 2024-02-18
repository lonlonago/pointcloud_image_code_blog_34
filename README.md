 ![avatar]( 20210331144845860.png) 

 Let me show you the visualization results first.  

#  First, the principle of the algorithm 

   Given n vertices in three-dimensional space, solve the convex hull surface composed of these n vertices. 

##  1. The solution process 

>  First, choose a tetrahedron (initial convex hull) formed by 4 points, and then add a new point P each time. There are two cases: 1. If P is in the convex hull, you can skip 2. If P is outside the convex hull, for a certain side, find the surface S containing the edge that can be "seen" from this point (whether it can be seen can be calculated with a normal vector to see if the point is outside the surface), delete these surfaces S, and then use the other two sides of S other than the edge to form two new surfaces with the point P. In this way, by traversing all the edges, P is added to the convex hull and a new convex hull is formed. Traverse all the points and finally get the convex hull of the entire point set. 

##  2. Find the area and volume 

>  setComputeAreaVolume (true);//set to true, then call the qhr library to calculate the total area and volume of the convex hull 

 It is important to note that the setComputeAreaVolume (true); line of code needs to be written before reconstruct ();, otherwise the area and volume will not be calculated. 

##  3. About convex hull display 

>  The convex hull calculated in Open3D is displayed in the form of a wireframe. Personally, I feel that the wireframe looks better, so I also use the wireframe display. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574257319
  ```  
#  III. Display of results 

 ![avatar]( 20210331144854781.png) 



--------------------------------------------------------------------------------

 regional growth 

 + 1. Algorithm principle 

 + 1. Algorithm flow 2. Algorithm overview 3. Reference 4. Core code

 + 2. Code implementation 

 + 3. Results display 

 + 4. Application cases 

 + 5. Display of results 

#  First, the principle of the algorithm 

##  1. Algorithm flow 

 ![avatar]( 20210516094422312.png) 

   The point cloud is sorted according to the curvature value of the points. The point with the smallest curvature is called the initial seed point. (1) The area growth algorithm starts from the seed point with the smallest curvature. The area where the initial seed point is located is the smoothest area. Starting from the area where the initial seed point is located can reduce the total number of segmented fragments, thereby improving the efficiency of the algorithm. (2) Set an empty clustering area C and an empty seed point sequence Q, and the clustering array L. (3) Select the initial seed point, add it to the seed point sequence Q, and search for the field point of the seed point, calculate the angle between the normal of each field point and the normal of the seed point, and when it is less than the set smoothing threshold, add the neighborhood point to C, and determine whether the curvature value of the field point is less than the curvature threshold. Add the field point smaller than the curvature threshold to the seed point sequence Q. After the neighborhood points are judged, delete the current seed point, and re-select a new seed point in Q. Repeat the above steps until the sequence in Q is empty and a region is grown. Add it to the clustering array L. (4) Use the curvature value to sort from small to large, select the input point set in sequence, and add the points as seed points to the seed point sequence, and repeat the above growth steps.  

##  2. Algorithm overview 

 The specific implementation method of the region growth algorithm (normal difference and curvature difference): 0. Calculate the normal and curvature curvatures, and sort according to the ascending curvature; 

##  4. Core code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574144585
  ```  
#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574144585
  ```  
#  III. Display of results 

 ![avatar]( 20200725204527581.png) 

 ![avatar]( 20200725204206322.png) 

#  IV. Application cases 

   Region growth segmentation is suitable for "plane" segmentation of point clouds with better planarity. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574144585
  ```  
#  V. Display of results 

 ![avatar]( c62f4ea58c5b4954bb5ab7989bc436b5.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

 ![avatar]( 20201217111213978.png) 

   As depicted in the figure, red is the overlapping area of the point cloud.  

 If a point has more than one point within a certain distance threshold area, it is considered to have duplicate points. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574159587
  ```  
#  III. Display of results 

 ![avatar]( 20201217111445690.png) 

#  CloudCompare 

 ![avatar]( 20210108213852922.gif) 



--------------------------------------------------------------------------------

 Sampling consistency algorithm 

#  First, the principle of the algorithm 

##  1. Algorithm flow 

 Input: Source point cloud 

 ![avatar]( 01c9db0420874ec4a7427f2efd70b75d.png) 

>  pcl::SampleConsensusInitialAlignmentpcl::Registration< PointSource, PointTarget, Scalar > Class 

>  These blogs about the sampling consistency algorithm are also well written!!! SAC-IA rough registration + NDT fine registration FPFH rough registration SAC-IA rough registration + ICP fine registration, detailed implementation process: SAC-IA algorithm implementation 

##  2. References 

>  [1] Rusu R B, Blodow N, Beetz M. Fast Point Feature Histograms (FPFH) for 3D registration [C]//IEEE International Conference on Robotics & Automation. IEEE, 2009. [2] Liu Yi. 3D reconstruction of binocular vision scenes combined with Kinect [D]. University of Electronic Science and Technology of China, 2016.p63 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574181543
  ```  
#  III. Display of results 

 ![avatar]( 20200712194750807.png) 



--------------------------------------------------------------------------------

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


--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Overview of the principle 

 pcl::SpinImageEstimation 

 ![avatar]( 20210529165010495.png) 

   Spin Image (rotated image) is a feature descriptor proposed by Johnson, which is mainly used for surface matching and model recognition in 3D scenes. As shown in Figure 1, on the model surface, there are fixed points and two wikis defined by their normal vectors, as well as tangent planes. Assuming any vertex on the model, it is now defined as the distance between the projected points on the plane, and its value is specified to be a real number greater than zero. It is the distance between the projected points on the plane, and it is determined to be positive or negative according to the upward or downward.  

 ![avatar]( 20210529165120340.png) 

 The process of calculating the Spin Image of a point is as follows: (1) a cylindrical coordinate system is built with a straight line parallel to the normal vector and passing through the fixed point p as the axis; (2) the vertices in the cylinder are projected onto the two-dimensional rotating image except the points. This process can be understood as a three-dimensional rotating image rotated 360 degrees around the normal vector. The points in the three-dimensional space swept by the three-dimensional rotating image will fall into the two-dimensional rotating image grid. The projection coordinates are (,), which is the one-dimensional index of the vertices; (3) According to the points falling into each grid in the two-dimensional rotating image, calculate the intensity of each grid, display the rotation, and use each grid (that is, pixels) as the image. The most direct method is to directly calculate the points that fall into each grid. However, in order to reduce the sensitivity to position, reduce the influence of noise and increase stability, Johnson uses bilinear interpolation to distribute a point into 4 pixels. Figure 2 shows a rotating image of three points on the model surface.  

##   3. Key parameters 

  1. Resolution, that is, the actual size of the two-dimensional mesh is the actual size of the pixel. It is more appropriate to use a size similar to that of the three-dimensional mesh. Therefore, the average value of all sides of the three-dimensional mesh is usually taken as the size of each mesh of the spinning image. The length and width of the mesh are usually defined as equal, that is, the side length, and the calculation formula of the side length: one side in the three-dimensional mesh model and the total number of sides in the three-dimensional mesh model. 

  2. Size, that is, the number of rows and columns of the spinning image, the two are generally equal. You can refer to the size 10x10 or 20x20, etc. 

 ![avatar]( 20200809194734617.jpg) 

  3.support angle, that is, the size limit of the angle included in the normal vector. The angle between the normal vector of the vertex in space and the normal vector of the selected point to create the cylindrical coordinate system. The effect is as follows: It can be seen that after the angle limit, those "pits (greater than 90 °) " equivalent to the section are eliminated, retaining the main information and reducing the subsequent calculation. The general angle limit range is between 60 ° - 90 °. 

##   4, spin image feature matching, similarity measurement and matching time point selection 

  1. The similarity measure 

 Use the following formula to calculate the similarity between two spinning images:  

   The number of pixels for each spin image is the inverse hyperbolic tangent function, and the input range is [-1, 1], which is interpreted in the original text as a typical statistical means. The range of values is [-1, 1], the more similar the two spin images are, the closer they are to 1, and the value is 1 when they are exactly the same. It can be seen that C is composed of two parts. The first part is the square of the value obtained by the inverse hyperbolic tangent function, and the second part is a weight λ multiplied by a smaller number. When the two spin images are similar, the proportion of the second part should be smaller. When they are not close, the proportion of the second part should be larger. The role of λ is to limit the matching of spin images when they are in low coincidence. The choice of λ in this paper is to list the number of non-empty pixels in all spin images in order of size and then take the median. This median is about the expected value of pixel overlap. Then take half of this median as λ considering the low overlap situation. 

 ![avatar]( 20200809194924268.jpg) 

 The matching between the 3D model and the scene is carried out in the following process. As shown in the figure above, after calculating the correlation coefficient, there will be a problem that for a point on the model, there may be more than one point in the scene that matches the features of the target point closely. The reason is the interference of the symmetrical part of the model or the points near the target point. Therefore, when determining the Plausible correspondences, filtering and multivariate group matching are required. Two filtering methods are given in this paper. 

 After determining the Plausible correspondences, the Plausible Transformation can be calculated. After that, the exact match can be obtained by using the ICP algorithm for exact matching. 

  2. Selection of model and scene matching points 

 At least three points must match between the two 3D models to determine a match. 

 Selection of three-dimensional field attractions: 

 Ensure uniform sampling by shape coding, and improve the probability of matching by selecting a spin image with an accurate normal vector. A perfect model without noise is generally enough to randomly select 10% of the points, and 1/20-1/2 is generally selected in practical application. 

 The method of similarity measure histogram is used to select the points of 3D model 

>  Summary: Spin Image has strong robustness against occlusion and background interference, and is widely used in point cloud registration and 3D target recognition. Its shortcomings are that it does not have scale invariance, requires large storage space, and requires point clouds to be evenly distributed. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574176815
  ```  
#  III. Display of results 

 ![avatar]( 2020080919505720.png) 



--------------------------------------------------------------------------------

 statistical filter 

 + 1. Statistical filtering 

 + 1. Algorithm overview 2. Calculation process 3. Main functions 4. References

 + 2. Code implementation 

 + 3. Results display 

 + 4. CloudCompare 

#  First, statistical filtering 

##  1. Algorithm overview 

   Laser scanning usually produces point cloud datasets with uneven density. In addition, errors in measurement can also produce sparse outliers. At this time, the calculation of local point cloud characteristics (such as normal vector or curvature change rate at the sampling point) is complicated, which will lead to wrong values, which in turn will lead to later processing failures such as point cloud registration. Statistical filters are used to remove obvious outliers. Outliers are often introduced by measurement noise, which is characterized by sparse distribution in space. It can be understood as: each point expresses a certain amount of information. The denser the points in a certain area, the greater the amount of information may be. Noise information is useless information and the amount of information is small. Therefore, the information expressed by outliers can be ignored. Taking into account the characteristics of outliers, it is possible to define a point cloud that is less than a certain density, i.e. the point cloud is invalid. Calculate the average distance from each point to its nearest (set) point. Then the distance between points in the point cloud should form a Gaussian distribution. Given the mean and variance, points can be excluded. 

##  2. Calculation process 

   Statistical analysis of the neighborhood of each point assumes that the distances of the points in the point cloud constitute a Gaussian distribution, the shape of which is determined by the mean and standard deviation. Let the coordinates of the first point in the point cloud be, and the distance from that point to any point is: Calculate the mean of the distance between each point traversed to any point as follows: Standard deviation is:  

 ![avatar]( 88e401e5602d43d19f3c796dfea6043d.png) 

   Let the standard deviation multiple be that only input is required during the implementation of the algorithm, and two thresholds are required. When a point is close and the average distance of points is within the standard range, the point is retained, and if it is not within the range, it is defined as outlier deletion.  

##  3. Main functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957429356
  ```  
>  Set the standard deviation multiplier to calculate the distance threshold. The numbers inside stddev_mult represent multiples of the standard deviation, and more than 1 standard deviation is an outlier. That is: the distance threshold will be equal to: (mean - stddev_mult * stddev, mean + stddev_mult * stddev). Points with an average neighborhood distance below or above this threshold will be classified as interior or outlier points. 

##  4. References 

>  [1] R.B. Rusu, Z.C. Marton, N. Blodow, M. Dolha, and M. Beetz. Towards 3D Point Cloud Based Object Maps for Household Environments Robotics and Autonomous Systems Journal (Special Issue on Semantic Knowledge), 2008. [2] Han Dongsheng, Xu Maolin, Jin Yuanhang. Filtering and Precision Analysis of Multi-source Heterogeneous Point Cloud Registration Data [J]. Journal of Mapping Science and Technology, 2020, 37 (05): 503-508. [3] PCL :: StatisticalOutlierRemoval class, realizes statistical filtering 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957429356
  ```  
#  III. Display of results 

 ![avatar]( 20210206202554434.jpg) 

>  If the running result cannot be displayed, click the mouse on the visual window, adjust the input method to the English state, and press the R key to reset the viewpoint. 



--------------------------------------------------------------------------------

#  I. References 

>  [1] Arun K S. Least-Squares Fitting of Two 3-D Point Sets [J]. Pattern Analysis & Machine Intelligence, 1987, 9. [2] Liu Yi. 3D Reconstruction of Binocular Visual Scene Combined with Kinect [D]. University of Electronic Science and Technology of China, 2016. [3] Zhang Bin. Research on Point Cloud Automatic Registration Method Based on Key Point Matching [D]. Minnan Normal University, 2020. P16-P20 [4] doc: Using a matrix to transform a point cloud [5] PCL: pcl :: regis tr a tion :: singular matrix factorization in the TransformationEstimationSVD class to find the transformation matrix, the input is the point coordinate of the same name and the output is the transformation matrix. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574114074
  ```  
#  III. Display of results 

 ![avatar]( 20200702211042775.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Overview of the principle 

   For a target point cloud with an unequal number of points in the source point cloud, two point sets with the number of points, some points in the source point cloud may not have a corresponding relationship in the target point set. Assuming that the minimum guarantee rate of data points that can be paired is P, (1) for each point of, find the nearest point in, and calculate the distance between each point pair; (2) in ascending order, select the first N point pairs and calculate their sum; (3) Exit if the constraint conditions (same as ICP) are met, otherwise continue; (4) Calculate the best transformation to minimize the error for the selected N pairs of corresponding points; (5) Transform and cycle. 

   The Trimmed ICP algorithm has been successfully applied to registrations with initial relative rotations up to 30 °. The algorithm always converges monotonically to a local minimum with respect to the pruned mean square error objective function. Convergence to a global minimum depends on the initial position of the point. To avoid local minima, it is common to run the ICP several times under different conditions. Alternatively, changing the value of running the Trimmed ICP under different conditions selects the best result. 

##  2. References 

>  [1] Chetverikov D, Svirko D, Stepanov D, et al. The Trimmed Iterative Closest Point Algorithm [C]//International Conference on Pattern Recognition. IEEE, 2002. [2] Li Xin, Moster, Huang Hua, Yang Shiji. Multi-source point cloud registration method for automatic calculation of overlap [J/OL]. Infrared and Laser Engineering: 1-10 [2021-05-16]. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574119298
  ```  


--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

   UniformSampling is the uniform sampling algorithm. Uniform sampling is the creation of a 3D voxel mesh on the input point cloud data (think of the voxel mesh as a set of tiny 3D boxes in space). Then, in each voxel (i.e. the 3D box), replace all points within that voxel with the point closest to the center of the voxel. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957413396
  ```  
#  III. Display of results 

 ![avatar]( 2020070609405182.png) 

#  IV. Source code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957413396
  ```  


--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Algorithm overview 

   Integral image is a method for performing normal estimation on ordered point clouds. The algorithm treats the point cloud as a depth image and creates certain rectangular regions on which the normals are calculated by taking into account the relationship between adjacent "pixels" (points) without running lookups on a search structure such as a KD tree. Therefore, its computational efficiency is very high, and the normals can usually be calculated in an instant. Therefore, it is best to use this method for real-time computation of ordered point clouds acquired from RGB-D sensors. Note: This method is only applicable to ordered point clouds!!! 

##  2. Main functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574179450
  ```  
 Set the normal estimation method. The algorithms currently implemented are: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574179450
  ```  
 Policies for setting processing boundaries. There are two strategies: BORDER_POLICY_IGNORE and BORDER_POLICY_MIRROR. 

##  3. References 

>  [1] doc:Normal Estimation Using Integral Images [2] PCL：pcl::IntegralImageNormalEstimation< PointInT, PointOutT >  [3] S. Holzer and R. B. Rusu and M. Dixon and S. Gedikli and N. Navab, Adaptive Neighborhood Selection for Real-Time Surface Normal Estimation from Organized Point Cloud Data Using Integral Images, IROS 2012. [4] D. Holz, S. Holzer, R. B. Rusu, and S. Behnke (2011, July). Real-Time Plane Segmentation using RGB-D Cameras. In Proceedings of the 15th RoboCup International Symposium, Istanbul, Turkey. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574179450
  ```  
#  III. Display of results 

 ![avatar]( 25409f54d3544bb39b24bf18282062fe.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Algorithm overview 

   The principle of GICP algorithm is to combine ICP algorithm and Point-to-plane ICP into a probabilistic framework model, perform point cloud registration based on this framework, and play a role similar to weights through the covariance matrix to eliminate the role of some bad corresponding points in the solution process. GICP has a wider application range than standard ICP, and under certain conditions, the GICP algorithm degenerates into a standard ICP algorithm. At the same time, if there is a unique solution, the minimum point is the global optimal solution, and the GICP algorithm degenerates into a standard ICP algorithm. 

##  3. References 

>  [1] Lin Baowei, Wang Fasheng, Sun Yi. Point cloud scale estimation and registration algorithm based on SGICP [J]. Computer Applications and Software, 2018, 35 (05): 202-207. [2] Generalized-ICP [C]//Robotics: Science and Systems V, University of Washington, Seattle, USA, June 28 - July 1, 2009. [3] PCL: pcl :: GeneralizedIterativeClosestPoint 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574150549
  ```  
#  III. Display of results 

>  Red and green are the initial positions, and blue and red are the registered positions. 

 ![avatar]( 20200714194638467.png) 



--------------------------------------------------------------------------------

#  Introduction to the method 

   Upsampling: Upsampling is a surface reconstruction method. When you have less point cloud data than you think, upsampling can help you restore the original surface (s). By interpolating the point cloud data you currently have, it is a complex process of guessing assumptions. So the built result will not be 100% accurate, but sometimes it is an alternative solution. So, when downsampling your point cloud, be sure to save a copy of the original data source! 

##  1. Implementation process 

   During the upsampling process, for each point, its local plane is sampled by creating points within a circle with a fixed radius and a fixed step size. Then, using the fitted polynomial, calculate the normal of this position and increase the displacement along the normal. The specific process is as follows: 

##  2. References 

>  [1] Wu Jian. A mobile least squares-based LiDAR point cloud encryption algorithm [J]. Urban Survey, 2019 (05): 110-115. [2] doc: Smoothing and normal estimation based on polynomial reconstruction [3] PCL: pcl :: Moving Least Squares class implements a mobile least squares-based point cloud upsampling 

#  Code implementation 

##  1. Only upsampling is performed 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574172551
  ```  
##  2. Simultaneous upsampling and calculation of normal vectors 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574172551
  ```  
#  III. Display of results 

 ![avatar]( 20201015201015462.png) 



--------------------------------------------------------------------------------

 + 1. Overview 2. Fitting plane 3. Implementation process 4. Model coefficients 5. Main functions 6. References

 + 2. Code example 

 + 3. Results display 

#  First, the principle of the algorithm 

##  1. Overview 

   The random sample consensus algorithm (RANSAC) is an iterative method for calculating the parameters of a mathematical model from a series of data containing divorced values. The RANSAC algorithm essentially consists of two steps, which are continuously looping: (1) randomly select the minimum number of elements that can form a mathematical model from the input data, and use these elements to calculate the parameters of the corresponding model. The selected number of these elements is the minimum number that can determine the parameters of the model. (2) Check which elements in all the data can conform to the model obtained in the first step. Elements that exceed the error threshold are considered outliers, and elements smaller than the error threshold are considered inliers. This process is repeated many times, and the model with the most points is selected to obtain the final result. 

##  2. Fitting plane 

>  RANSAC is specific to the fitting plane in the spatial point cloud: 1. Three points are randomly selected from the point cloud. 2. These three points form a plane. 3. Calculate the distance from all other points to the plane. If it is less than the threshold T, it is considered to be a point in the same plane. 3. If there are more than n points in the same plane, save the plane and mark all points on this plane as matched. 4. The condition for termination is that the plane found after N iterations is less than n points, or three unmarked points cannot be found. 

##  3. Implementation process 

   At present, the most common and simplest method to fit a plane is least squares fitting, but the accuracy of least squares fitting is easily affected by noise. The random sampling consensus algorithm (RANSAC) can eliminate the influence of noise through iterative fitting, and the fitting accuracy is greatly improved. The random sampling consensus algorithm process is shown in Figure 1:1. From the mathematical knowledge, it is known that at least three points are required to fit the plane, so three points are randomly selected first, and then the plane model parameters are calculated according to the plane equation (1). 2. Use the remaining data points to test the plane model estimated in (1), calculate the result error, and compare the error with the set error threshold. If it is less than the set threshold, determine the point as the inner point, and count the number of inner points under the parameter model and record it. 3. Continue with steps 1 and 2. If the number of inner points of the current model is greater than the maximum number of inner points that have been saved, update the model parameters. The retained model parameters are always the model parameters with the largest number of inner points. 4. Repeat steps 1 to 3 and iterate until the iteration threshold is reached. Find the model parameters with the largest number of inner points. Finally, use the inner points to estimate the model parameters again to obtain the final model parameters. 

 ![avatar]( 20210516154607138.png) 

##  4. Model coefficients 

 The plane model coefficients are defined as: 

##  5. Main functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574170015
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574170015
  ```  
##  6. References 

>  [1] Wang Shaochen. Research on the measurement method of workpiece curved surface profile based on point cloud reconstruction technology [D]. Shandong University, 2020. [2] doc: Plane model segmentation [3] PCL: pcl :: SampleConsensusModelPlane 

#  Code example 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574170015
  ```  
#  III. Display of results 

>  The left side is the original point cloud, and the right side is the extracted plane point cloud 

 ![avatar]( 20210312212312155.png) 



--------------------------------------------------------------------------------

#  I. Overview 

    The call function that comes with PCL can directly view the valid attribute information contained in the point cloud data, such as RGB, XYZ, normal vector, etc. The following code shows how to get 

##  1. Main function 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957427841
  ```  
##  2. Algorithm source code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957427841
  ```  
#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957427841
  ```  
#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957427841
  ```  
>  RGB: color information 

>  normal_x normal_y normal_z: scrap scrap 

>  X y z _: 3D coordinates 

 Other properties, and so on. 



--------------------------------------------------------------------------------

##  First, the code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574144662
  ```  
##  II. Display of results 

 ![avatar]( 20201016205004407.png) 

##  Third, grid plus color 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574144662
  ```  
##  IV. Display of results 

 ![avatar]( 20201016210620664.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

   The geometric structure of a point cloud is not only the macroscopic geometry, but also its microscopic arrangement, such as similar dimensions in the horizontal direction and the same distance in the vertical direction. If the point cloud is collected with high-resolution cameras and other equipment, the point cloud will often be denser. Excessive number of point clouds will make subsequent segmentation difficult. The voxel grid filter can achieve the function of downsampling without destroying the geometric structure of the point cloud itself. Although random downsampling is more efficient than voxel filters, it will destroy the microstructure of the point cloud. The use of voxelization mesh method to achieve downsampling can reduce the number of points and save the shape characteristics of the point cloud. It is very practical in improving the speed of algorithms such as registration, surface reconstruction, and shape recognition. 

##  1、VoxelGrid 

>  PCL :: Voxel Grid is to create a three-dimensional voxel grid by the input point cloud data, each voxel with the center of gravity of a point in the voxel to approximately display other points in the voxel, so that all points in the voxel are finally represented by a center of gravity, and the filtered point cloud is obtained after processing all voxels. This method is slower than the method of approximating the voxel center (note the center and center of gravity), but it is more accurate for the representation of the surface corresponding to the sampling point. 

##  2, ApproximateVoxelGrid type parameter analysis 

>  PCL :: ApproximateVoxelGrid is to create a three-dimensional voxel grid through the input point cloud data, and use the center of all points in each voxel to approximate other points in the voxel. This method of computing the center is based on a hash function. For large-scale scenic spots with huge amounts of data, it is much faster than the VoxelGrid voxel filter to calculate the centroid of all points in the voxel. 

##   3. VoxelGrid calculation process 

 ![avatar]( 20210307103542835.png) 

 1. Find the maximum and minimum values on the three coordinate axes according to the coordinate set of the point cloud data. 2. Set the side length of the voxel small grid. 3. Find the side length of the minimum bounding box of the point cloud according to the maximum and minimum values on the three coordinate axes. 4. Calculate the size of the voxel grid. 5. Calculate the index of each point cloud in the voxel small grid  

       6. Sort the elements in order from smallest to largest, calculate the center of gravity of each voxel small grid, and replace all points in the small grid with the center of gravity. 

#  Code implementation 

##  1. VoxelGrid complete code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
##  2. Function analysis 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 empty constructor 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 destructor 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Set the size leaf_ voxel grid by vector. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 The dimensions of the voxel grid in the three directions of XYZ are respectively set by lx.ly. Iz. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets the vector that sets the voxel grid. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Sets whether to downsample all fields. If you need to downsample all fields, set the parameter downsammple to True, and only downsample XYZ fields to False. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets the Boolean value of whether to downsample all fields. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Sets the minimum number of points required for the voxels to be used. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Obtain the minimum number of points required for the voxels to be used. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Set the parameter save._leaf_layout to true if you need to save leaf structure information for future access, otherwise false. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets a Boolean value to hold leaf structure information. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 After filtering, the function obtains the smallest coordinates in the three directions of the bounding box. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 After filtering, the function obtains the maximum coordinates in the three directions of the bounding box. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 After filtering, the points in three directions are obtained. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 After filtering, the function obtains the product coefficients between the voxel index and the three directional fractions. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets the one-dimensional index of the point p under the voxel grid coordinates. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Returns the index in the downsampled cloud of the result of the point at the specified raster coordinates relative to the raster coordinates of the specified point (-1 if the cell is empty/out of bounds). 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Returns the layout of the leaves for quick access to cells relative to the current position. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Returns the voxel (i, j, k) grid coordinates corresponding to a (x, y, z) coordinate point. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Returns the index in the downsampled cloud corresponding to a given set of coordinates. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Sets the name of the field to be used to filter the data. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets the name of the field used for filtering. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Set field limits for filtering 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Get filtered field limits 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Sets whether you need to return data outside the interval specified by setFilterLimits (min, max), if you need to return it, set limit_negative to true. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets a Boolean value for data outside the interval specified by setFilterLimits (min, max). 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets a Boolean value for data outside the interval specified by setFilterLimits (min, max). 

##  3, ApproximateVoxelGrid complete code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
##  4. Function analysis 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 empty constructor 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 copy constructor 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 destructor 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Define operator overloaded functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Set the voxel raster leaf size, the vector parameter leaf_size is the voxel raster leaf size parameter, and each element represents the size of the voxel in the XYZ direction. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Ditto, lx, ly, lz are set voxel size in the XYZ direction. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Obtain setting voxel raster leaf size parameter. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Sets whether to downsample all fields. Different point types contain different numbers of fields. When downsampling, most of them downsample spatial XYZ, and some fields are also meaningful when downsampling, such as color, intensity, etc. If you need to downsample all fields, set it to True, and only for XYZ fields, set it to False. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 Gets the status of the internal downsampling parameter (true if all fields need to be downsampled, false if only XYZ). 

#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 ![avatar]( 87bef3a0d3ca4ad4994cc55b781876b4.png) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574236763
  ```  
 ![avatar]( eab6aa0661e441e6aad2273b0692c195.png) 



--------------------------------------------------------------------------------

#  I. Overview of algorithms 

   The VoxelGrid class and ApproximateVoxelGrid class of PCL implement the voxel-based filtering method to downsample the point cloud. The octree also establishes voxels, so the voxels based on the octree can also downsample the point cloud. There are ready-made functions in PCL to solve the voxel center of the octree, so the easiest way is to replace the point in each voxel with the voxel center of the octree, so as to realize the downsampling of the point cloud. 

>  Note: This method is basically the same as ApproximateVoxelGrid, replacing the points in the voxels with the center points. The only difference is that ApproximateVoxelGrid can freely set the length, width and height of the voxels, while the octree can only be the voxels that build the cube. 

   The code also implements the improvement of octree voxel filtering, that is, replacing the voxel center point with the point closest to the voxel center point, so that the points after downsampling are still points in the original point cloud data. 

#  Code implementation 

 octree_sample.h 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574147183
  ```  
 octree_sample.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574147183
  ```  
 main.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574147183
  ```  
#  III. Display of results 

 ![avatar]( 20210219181834714.png) 

 1. Use the voxel center point of the octree to streamline the original point cloud (this center point may not be a point in the point cloud) 2. Use the nearest neighbor point of the voxel center point of the octree to streamline the original point cloud (the final point cloud is still a point in the original point cloud data)  



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

  The vtkMassProperties class can calculate the surface area and volume of triangular meshes, but the mesh must be closed triangular mesh data. For non-triangular meshes, the mesh needs to be converted to triangular mesh data. vtkTriangleFilter can convert polygonal mesh data to triangular mesh data. The use of this class is very simple, just set the vtkPolyData mesh data that needs to be converted as input. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574176051
  ```  
#  III. Display of results 

 ![avatar]( 20201216170153205.png) 

#  CloudCompare 

 ![avatar]( 2020122909411588.gif) 

 Implementation in CloudCompare software  

#  V. Experimental data 

 Link: https://pan.baidu.com/s/1mLe5X6YCsxwdHrZ6Ua8qzA Extraction code: h74h 



--------------------------------------------------------------------------------

 + 1. Read the .ply file 

 + 1. Save the .ply file 

#  Read the .ply file 

    ReadPLY is a built-in mesh model reading function in VTK. This function only supports mesh data in .ply format and does not support reading point cloud data in .ply format. 

##  1. Code example 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574127151
  ```  
##  2. Results display 

 ![avatar]( f9a35eb27c6e46a0bc9cfd8498d62ec4.png) 

#  Save the .ply file 

    WritePLY cannot save the colors of a model, and unlike vtkPolyDataXMLWriter and most other VTK writers, to write colors to a .ply file, you must specify the use of vtkPLYWriter: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574127151
  ```  
##  1. Code example 

 Color preservation is not considered here. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574127151
  ```  
##  2. Results display 

 ![avatar]( 6f44ebbf7d4f4eaba99074deba645a8e.png) 



--------------------------------------------------------------------------------

