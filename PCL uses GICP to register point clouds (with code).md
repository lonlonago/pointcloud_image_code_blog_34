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

