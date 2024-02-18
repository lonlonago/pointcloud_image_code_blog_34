 + 1. Read the .ply file 

 + 1. Save the .ply file 

#  Read the .ply file 

    ReadPLY is a built-in mesh model reading function in VTK. This function only supports mesh data in .ply format and does not support reading point cloud data in .ply format. 

##  1. Code example 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574127151
  ```  
##  2. Results display 

 ![avatar]( f9a35eb27c6e46a0bc9cfd8498d62ec4.png) 

#  Save the .ply file 

    WritePLY cannot save the colors of a model, and unlike vtkPolyDataXMLWriter and most other VTK writers, to write colors to a .ply file, you must specify the use of vtkPLYWriter: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574127151
  ```  
##  1. Code example 

 Color preservation is not considered here. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574127151
  ```  
##  2. Results display 

 ![avatar]( 6f44ebbf7d4f4eaba99074deba645a8e.png) 

