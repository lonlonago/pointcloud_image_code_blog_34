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
