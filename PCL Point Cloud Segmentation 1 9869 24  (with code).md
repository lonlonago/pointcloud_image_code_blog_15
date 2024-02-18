Point cloud segmentation is based on spatial, geometric, and textural characteristics to divide point clouds, so that point clouds within the same division have similar characteristics. Effective segmentation of point clouds is often a prerequisite for many applications, such as reverse work, CAD segmentation of different scanning surfaces of parts, and then better reconstruction of cavity repair surfaces, feature description and extraction, and then retrieval based on 3D content, combined reuse, etc. 

 Case Study 

 Use a set of point cloud data for simple plane segmentation: 

 planar_segmentation.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573791
  ```  
 The results are as follows: The data to start printing is manually added point cloud data, not all of which are on the plane where z is 1. After the processing of dividing the object, all internal points are extracted, that is, the point set where z is not equal to 1 is filtered out 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzE0MjY1OTQwNy0xNzY2NjU1Njk2LnBuZw) 

 (2) Segmentation of cylinder model: A cylinder model is extracted from a point cloud with noise using random sampling consensus estimation. 

 New file cylinder_segmentation cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573791
  ```  
 The results of the trial printing are as follows 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzE0MzM1NTExMC0xNDY3NjgwMjI1LnBuZw) 

 The result of the original point cloud visualization. There are planes, cups, and other objects in the 3D scene 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzE0NDYyNzMxMy0xMzM3NDc1ODgucG5n) 

 Generate the split plane and cylindrical point clouds, and the viewing results are as follows 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzE0NDczMTk3MC01MzAyMTc1MzUucG5n) 

 (3) Realize Euclidean clustering extraction in PCL. Segment the scene composed of 3D point clouds 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573791
  ```  
 Run result: 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzE0NTAxNDk3MC0xMTE2Mzk0OTMucG5n) 

 No longer look at the visualized results one by one 

 In order to be more practical, I will combine these basic programs with actual examples, because these are all official examples. I will learn them first, at least once, so that it will be easier to combine them with actual applications later. (Because I also learn while learning, and then go back and improve on the foundation.) 

