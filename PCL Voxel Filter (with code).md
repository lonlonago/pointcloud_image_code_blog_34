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

