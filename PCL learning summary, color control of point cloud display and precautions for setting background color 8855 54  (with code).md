  SetBackgroundColor 

 Display the color information that comes with the point cloud (PointCloudColorHandlerRGBField) 

  Color according to a field of the point cloud (PointCloudColorHandlerGenericField) 

  Custom single color (PointCloudColorHandlerCustom) 

 Random coloring (PointCloudColorHandlerRandom) 

 In the process of using PCLVisualizer to display point clouds, it is often necessary to color point clouds to distinguish between different types of point clouds. The coloring methods often used are: 

>  1. Display the color information that comes with the point cloud; 2. Color according to a certain attribute (field) of the point cloud (for example: different colors in X, Y, Z, etc.); 3. Customize a single color (display the same color to a point cloud); 4. Random coloring (randomly assign a single color to the point cloud by the compiler); 

#   SetBackgroundColor 

 So if you want to set the background color to the specified rgb value, you need to divide by 255: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573796601
  ```  
 To set RGB to (125, 100, 200), the background color should be as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573796601
  ```  
#  Display the color information that comes with the point cloud (PointCloudColorHandlerRGBField) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573796601
  ```  
 A class "PointCloudColorHandlerRGBField" is used here. In fact, it is a bit redundant to display the built-in color information of the point cloud in this way. You can directly "viewer- > addPointCloud (cloud," sample cloud ");" to achieve the above functions. 

#   Color according to a field of the point cloud (PointCloudColorHandlerGenericField) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573796601
  ```  
 Common fields are: 

>  xyznormal_x (normal in the X direction) normal_y (normal in the Y direction) normal_z (normal in the Z direction) rgb (color) curvature (curvature) 

#   Custom single color (PointCloudColorHandlerCustom) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573796601
  ```  
 The function of this class is to give the same color to points in the same point cloud, which is used to distinguish different point clouds in the same window. It is worth noting that the value range of rgb is not [0, 1] but [0, 255], otherwise the point cloud will be black. 

#  Random coloring (PointCloudColorHandlerRandom) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573796601
  ```  
 The system randomly selects a single color for coloring. 

