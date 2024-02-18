(1) Implementation of point cloud to depth map and visualization 

 The essential difference between a point cloud and a depth map 

 1. Depth image is also called distance image, which refers to the distance (depth) value from the image collector to each point in the scene as the pixel value of the image. Obtaining methods include: LiDAR depth imaging method, computer stereoscopic vision imaging, coordinate measuring machine method, moire fringe method, structured light method. 2. Point cloud: When a beam of laser light shines on the surface of an object, the reflected laser light will carry information such as orientation and distance. If the laser beam is scanned according to a certain trajectory, the reflected laser point information will be recorded while scanning. Due to the extremely fine scanning, a large number of laser points can be obtained, so a laser point cloud can be formed. Point cloud formats include * .las; * .pcd; * .txt, etc. The depth image can be calculated as point cloud data after coordinate transformation; the point cloud data with rules and necessary information can be inverted into depth image 

 The rangeimage is a regular depth map with basic information such as focal length obtained from a 3D scene captured by a sensor at a specific angle. 

 The pixel value of the depth image represents the distance or depth value from the sensor to the object. 

 The RangeImage class inherits the main function of PointCloud to achieve a depth image of a 3D scene obtained from a specific viewpoint. The inheritance relationship is 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMjE1MDY0ODY1OC0xMjY1NTM2MjY5LnBuZw) 

 So we know that there are rules and necessary information that can be converted into depth images. Then we can directly create an ordered and regular point cloud, such as a plane, or we can directly use the point cloud obtained by Kinect to visualize the depth map, so first analyze the transformation of point cloud to depth map in the program. (The comments of the program are my own understanding, and the comments are more detailed) 

 Explain in great detail in the code, compile to view the results 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMjE1NDkzNjQyNC0xMjI5NzI4Nzg5LnBuZw) 

                                              No results for entering a PCD point cloud file 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMjE1NDk1OTY3NC0yMDY3MTY2OTM3LnBuZw) 

                                                                    Enter the original image of the point cloud 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMjE1NDkxMzA4MC0yMDYyODAxNjk0LnBuZw) 

                                                                         The input result and its depth map 

 (2) How to extract boundaries from depth images 

   Extracting the boundary from the depth image (defined as the boundary from the position where the foreground crosses to the background), for the object boundary: this is the outermost layer of the object and the visible point set of the shadow boundary, the shadow boundary: the point set adjacent to the occluded background, the Veil point set, the interpolation point between the occluded object boundary and the shadow boundary, they are typical data types in 3D distance data acquired by lidar. The boundaries of these three types of data and depth images are shown in the figure: 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAyLzk3NjM5NC0yMDE3MDIyNzE5MzMxMDE3My0yMTI2ODE1NTkwLnBuZw) 

 Code analysis: Read the point cloud from the disk, create a depth image and visualize it, and extract boundary information. It is important to distinguish between the geometry of the current viewpoint invisible point in the depth image and the point set that should be visible but outside the sensor acquisition distance range. The latter can be marked as a typical boundary, but the current viewpoint invisible point cannot be a boundary. Therefore, if the latter measurement value exists, providing those data beyond the sensor distance acquisition range is very important for boundary extraction. 

 New file range_image_border_extraction cpp: 

 The result of the compiled run./range_image_border_extraction -m 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAyLzk3NjM5NC0yMDE3MDIyNzE5NTQzNDUxNi03NjY1NzczNDIucG5n) 

 This will be a custom-generated, rectangular floating-point point cloud, and the display results can be seen that the detected boundaries are represented by the larger green points, and the other points are represented by the default normal size points. 

 To be continued *****************8888888 

