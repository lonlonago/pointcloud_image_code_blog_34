 ![avatar]( 20210331144845860.png) 

 Let me show you the visualization results first.  

#  First, the principle of the algorithm 

   Given n vertices in three-dimensional space, solve the convex hull surface composed of these n vertices. 

##  1. The solution process 

>  First, choose a tetrahedron (initial convex hull) formed by 4 points, and then add a new point P each time. There are two cases: 1. If P is in the convex hull, you can skip 2. If P is outside the convex hull, for a certain side, find the surface S containing the edge that can be "seen" from this point (whether it can be seen can be calculated with a normal vector to see if the point is outside the surface), delete these surfaces S, and then use the other two sides of S other than the edge to form two new surfaces with the point P. In this way, by traversing all the edges, P is added to the convex hull and a new convex hull is formed. Traverse all the points and finally get the convex hull of the entire point set. 

##  2. Find the area and volume 

>  setComputeAreaVolume (true);//set to true, then call the qhr library to calculate the total area and volume of the convex hull 

 It is important to note that the setComputeAreaVolume (true); line of code needs to be written before reconstruct ();, otherwise the area and volume will not be calculated. 

##  3. About convex hull display 

>  The convex hull calculated in Open3D is displayed in the form of a wireframe. Personally, I feel that the wireframe looks better, so I also use the wireframe display. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574257319
  ```  
#  III. Display of results 

 ![avatar]( 20210331144854781.png) 

