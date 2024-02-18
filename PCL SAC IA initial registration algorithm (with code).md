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

