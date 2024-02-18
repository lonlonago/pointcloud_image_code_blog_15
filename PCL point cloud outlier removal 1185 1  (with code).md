#  Statistical outlier removal 

 Principle: Traverse the point cloud, calculate the average distance between each point and its k nearest neighbor points, and then calculate the mean and standard deviation of all average distances. The distance threshold can be expressed as, α is a scaling coefficient, and once again traverse the point cloud, points with an average distance greater than k neighbor points are marked as outliers. 

 ![avatar]( 5d8ad0f8a3cb4f91af010f6891bbbdc9.gif) 

 Effect display:  

#  Radius outlier removal 

 Principle: Count the number of points in the neighborhood of a sphere with a radius from a point. If it is less than nb_points, mark the point as an outlier. Effect display: 

 ![avatar]( bc8d8008a361425ea343259ec4f233c0.gif) 

#  C++ code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573717226
  ```  
