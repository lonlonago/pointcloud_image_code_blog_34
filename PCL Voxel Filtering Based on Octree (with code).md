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

