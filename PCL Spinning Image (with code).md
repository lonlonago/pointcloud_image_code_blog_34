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

