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

