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

