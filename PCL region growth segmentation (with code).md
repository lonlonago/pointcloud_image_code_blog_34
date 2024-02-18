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

