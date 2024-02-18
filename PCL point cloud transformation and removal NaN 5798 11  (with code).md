 ![avatar]( 976394-20170308153401875-491746160.png) 

 ![avatar]( 976394-20170308153534266-1556966551.png) 

 And so on. Model. 

 Here, directly use the program to realize the rotation of a point cloud, and create a new file matrix.cpp 

 After compilation, we can find any PCD file to view the effect, or we can view the results of different parameters with the parameters of the program 

 The result printed by the command window 

 ![avatar]( 976394-20170308155248172-622820128.png) 

 Visual results 

 ![avatar]( 976394-20170308155315859-565040524.png) 

  (2) Removal 

 The point cloud obtained from the sensor may contain several measurement errors and/or inaccuracies. One of them is the presence of NaN (not number) values in the coordinates of some points, as you can see in the file below: 

  The member function of the point cloud object is called "is_dense () ", which returns true as a finite value if all points are valid. A NaNs indicates that there is a problem with measuring the distance of the sensor to the point, possibly because the sensor is too close or too far away, or because of surface reflections. Then when there are NaNs values of invalid point clouds as input to the algorithm, it may cause many problems, such as "If such an error occurs and these points are removed, then the following is the program to solve the problem of removing invalid points 

 Then you can display the visual after removing the NaNs points, 

 ![avatar]( 976394-20170308201045281-1758610323.png) 

  This point cloud is my own point cloud generated with kinect. When NaNs are not removed, you can read the following to display their point cloud values. In the command window, you will find that there will be many invalid points of NaNs 

 After removing these dots, there will be no invalid points of NaNs in the result of reading some prints, so that there will be no errors in the later use of the algorithm. 

 ![avatar]( 976394-20170308201359016-786594939.png) 

 The problem with this approach is that it does not keep the point cloud still an ordered point cloud. All point clouds store a "width" and "height" variable. In an unordered point cloud, the total is the same width, while the height is set to 1. In an ordered point cloud (like a camera shot from a camera sensor such as Kinect or Xtion), the image resolution sensor works with pixels of the same width and height. The point cloud is distributed among the rows of the depth image, and each point corresponds to a pixel. Member function "isorganized () " Returns true if the height is greater than 1. Since removing the NaNs invalid point changes the number of points in the point cloud, it can no longer maintain the organization with the original aspect ratio, so the function will set the height to 1. This is not a big problem. Only a few PCL algorithms work explicitly with ordered point clouds (most of which are used for optimization), but you must consider the implications. 

 That's it for now... 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303135500376-706958186.jpg) 

