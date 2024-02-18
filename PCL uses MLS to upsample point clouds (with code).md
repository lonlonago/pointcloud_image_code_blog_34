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

