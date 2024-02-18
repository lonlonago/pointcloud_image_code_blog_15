The current depth image acquisition methods include lidar depth imaging, computer stereoscopic vision imaging, coordinate measuring machine method, moire fringe method, structured light method, etc. The research focus of depth images is mainly concentrated in the following aspects, depth image segmentation technology, depth image edge detection technology, multiple depth images based on different viewpoints registration technology, three-dimensional reconstruction technology based on depth data, three-dimensional target recognition technology based on three-dimensional depth images, multi-resolution modeling of depth images and geometric compression technology, etc. The main difference between depth images and point clouds in PCL is that the retrieval methods of their nearest neighbors are different, and they can be converted to each other. 

 (This chapter is very important to me.) 

 Introduction to module RangeImage related concepts and algorithms 

 Depth images, also known as range images, refer to images that use the distance value from the image collector to each point in the scene as the pixel value. It directly reflects the geometry of the visible surface of the scene. It can be used to easily solve many problems in 3D object description. Depth images can be calculated as point cloud data after point cloud transformation. Point cloud data with rules and necessary information can be inverted into depth image data 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAyLzk3NjM5NC0yMDE3MDIyNzE0MzQxNDE3My0zMDE1NTkzMTgucG5n) 

 The process of obtaining depth images from different perspectives: 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAyLzk3NjM5NC0yMDE3MDIyNzE0MzQ0MDIwNC05NTYzNTc4Ni5wbmc) 

    (1) Introduction to the module RangeImage related classes in PCL 

  pcl_range_image library contains two expression depth image and depth image operation class, which depends on the PCL :: common module, the depth image (distance image) pixel value represents the distance and depth from the sensor to the object, the depth image is a three-dimensional representation of the object, generally obtained by a stereo camera or a ToF camera, if the camera has internal calibration parameters, the depth image can be converted into a point cloud 

 1.class pcl::RangeImage 

     The RangeImage class inherits from PointCloud, and its main function is to achieve a depth image of a 3D scene from a specific viewpoint. Its inheritance relationship is as follows: 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAyLzk3NjM5NC0yMDE3MDIyNzE0NTAzMjExMC04MTY1NzkucG5n) 

 The members of the class RangeImage are: 

 (For a detailed explanation, please check the official website.)        

   (2)class pcl::RangeImagePlanner              

 RangeImagePlanner is derived from the original depth image, but it is different from the original depth image because it does not use spherical projection, but instead projects through a plane projection (cameras generally use this projection method). Therefore, it is more practical for existing depth images acquired by depth sensors. The inheritance relationship of the class is as follows: 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAyLzk3NjM5NC0yMDE3MDIyNzE2MTIzNzc4Mi0xODQ1NzQ3MTY1LnBuZw) 

     Wait, see the official website for details. 

 (3) Application examples 

  How to create a depth map from a point cloud, how to create a depth image from a point cloud and the location of a given sensor, this procedure is to generate a rectangular point cloud and then create a depth image based on that point cloud 

 New file range_image_creation cpp: 

 Show results 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAyLzk3NjM5NC0yMDE3MDIyNzE3MjYzNDkyMy04NTIyODQ0MzcucG5n) 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzEzNTExMTQ3MC0xODkwMDY4MDIwLmpwZw) 

  To be continued ******************************88888 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

Regarding the input of a specific object point cloud, find a match with the object point cloud from the scene, this method can be used to grab the specified object, etc. The specific code is explained as follows. 

 Specific code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573786115
  ```  
 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyNDE4MTc1ODU0OS0xNjEwODExNDc0LnBuZw) 

  Visualize feature corners   

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyNDE4MTgyMTAxOC0xMDYxMjc0MTgyLnBuZw) 

  Ways to use Hough-registered corners 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzA0Lzk3NjM5NC0yMDE3MDQwMzEyNDAzNDYyOC0xMTUzNjI1NzUucG5n) 



--------------------------------------------------------------------------------

  Key points are proposed to identify objects from depth images, and the extraction process of NARF key points has the following requirements: 

       A) The extraction process takes into account the edge and surface change information of the object. 

       B) Key points can be repeatedly detected at different viewing angles. 

       c) 

      ： 

       (1) Traverse each depth image point and perform edge detection by looking for locations with depth changes in nearby regions. 

       (2) Traverse each depth image point and determine a coefficient to measure the surface change and the main direction of the change according to the surface change of the neighboring region. 

       (3) 

       (4) Smooth filtering of interest values. 

       (5) The final key point found without maximum compression is the NARF key point. 

  For a more detailed description of NARF, check out this blog www.cnblogs.com/ironstark/p/5051533.html. 

 Introduction to keypoints modules and classes in PCL 

 (1) class pcl :: Key point < PointInT, PointOutT > class keypoint is the base class for all key point detection related classes, defines the basic interface, and the specific implementation is completed by the subclass. The inheritance relationship is as follows: 

 ![avatar]( 976394-20170227202611751-419364054.png) 

 Specific introduction: 

 （2）class  pcl::HarrisKeypoint2D<PointInT,PointOutT,IntensityT> 

      The HarrisKeypoint2D class implements the Harris keypoint detector based on the intensity field of the point cloud, which includes a variety of different variations of the Harris keypoint detection algorithm. The key functions are described as follows: 

 （3）pcl::HarrisKeypoint3D< PointInT, PointOutT, NormalT > 

 HarrisKeypoint3D (ResponseMethod method=HARRIS, float radius=0.01f, float threshold=0.0f)   

  case analysis 

 The experiment realizes the extraction of NARF key points, and visualizes them with images and 3D display, which can intuitively observe the position and number of key points narf_feature_extraction: 

 Run result: 

 ![avatar]( 976394-20170227224904407-689735214.png) 



--------------------------------------------------------------------------------

 The principle of implementing octree  

 　　(1). Set the maximum recursion depth. 

 　　Find the maximum size of the scene and create the first cube with that size. 

 　　(3). Throw the unit element into a cube that can be contained and does not have a sub-node. 

 　　(4). If the maximum recursion depth is not reached, it is subdivided into eight equal parts, and then all the unit elements contained in the cube are distributed to the eight sub-cubes. 

 　　(5). If it is found that the number of unit elements assigned to the child cube is not zero and the same as the parent cube, then the child cube stops being subdivided, because according to the theory of space division, the subdivided space must be allocated less. If the number is the same, then the number of cuts is still the same, which will cause infinite cuts. 

 　　Repeat 3 until the maximum recursion depth is reached. 

 The logical structure of an octree is as follows: 

 Introduction of Octree module and class in PCL 

 PCL :: octree :: Octree 2B uf Base < LeafContainerT, BranchContainerT > realizes the simultaneous storage and management of two octree and memory, which can efficiently realize the establishment and management of octree and other operations, and the node realizes the detection of the structure of the adjacent tree nodes, corresponding to the spatial point cloud, which can detect the dynamic changes of the spatial surface, which is very useful in the detection of spatial dynamic changes 

  更多 docs.pointclouds.org/trunk/classpcl_1_1octree_1_1_octree2_buf_base.html#aeea7ecfd6ebe82e93d3c7bb869355502  

 application example 

 Point clouds are composed of massive datasets that describe three-dimensional points in space by distance, color, normals, and other additional information. In addition, point clouds can also be created at very high speed, so they require considerable storage resources. Once a point cloud needs to be stored or transmitted over a rate-limited communication channel, it becomes very useful to provide a compression method for this data. PCL provides a point cloud compression function, which allows coding to compress all types of point clouds. 

 ![avatar]( compression_tutorial.png) 

 New project ch3_2, new file point_cloud_compression cpp 

  The result of running after compilation is as follows: 

 The picture shows the real-time visualization result with RGB texture information. The scaling visualization result shows that the point cloud is resampled after compression, and the texture information is lost, but the amount of data is reduced. In practical applications, a trade-off is required 

 ![avatar]( 976394-20170225125350913-44896194.png) 

 At the same time, in the process of compression and decompression, because compressedData is set to true, the compression rate frame number and other information are printed on the standard output: 

 ![avatar]( 976394-20170225125408195-1064120255.png) 

 Compression profile: The compression profile defines the parameter set for the PCL point cloud encoder and is optimized for compressing the ordinary point cloud obtained from the openNI collector. Note that the decoding object does not need to be represented by parameters, because it detects and obtains the corresponding encoding parameter configuration during decoding, such as the following compression profile 

 LOW_RES_ONLINE_COMPRESSION_WITHOUT_COLOR,//Respect rate of 1 cm ^ 3 no color, fast online coding LOW_RES_ONLINE_COMPRESSION_WITH_COLOR,//Respect rate of 1 cm ^ 3 with color, fast online coding MED_RES_ONLINE_COMPRESSION_WITHOUT_COLOR,//Respect rate of 5 mm ^ 3 no color, fast online coding MED_RES_ONLINE_COMPRESSION_WITH_COLOR,//Respect rate of 5 mm ^ 3 with color, fast online coding HIGH_RES_ONLINE_COMPRESSION_WITHOUT_COLOR,//Respect rate of 1 mm ^ 3 no color, fast online coding HIGH_RES_ONLINE_COMPRESSION_WITH_COLOR,//Respect rate of 1 mm ^ 3 with color, fast online coding LOW_RES_OFFLINE_COMPRESSION_WITHOUT_COLOR,//Respect rate of 1 cm ^ 3 no color, efficient offline coding LOW_RES_OFFLINE_COMPRESSION_WITH_COLOR,//The resolution is 1 cm ^ 3 with color, efficient offline coding MED_RES_OFFLINE_COMPRESSION_WITHOUT_COLOR,//The resolution is 5 mm ^ 3 without color, efficient offline coding MED_RES_OFFLINE_COMPRESSION_WITH_COLOR,//The resolution is 5 mm ^ 3 with color, efficient offline coding HIGH_RES_OFFLINE_COMPRESSION_WITHOUT_COLOR,//The resolution is 1 mm ^ 3 without color, efficient offline coding HIGH_RES_OFFLINE_COMPRESSION_WITH_COLOR,//The resolution is 1 mm ^ 3 with color, efficient offline coding MANUAL_CONFIGURATION//Allows manual configuration for advanced parameterization 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303134619891-462981285.jpg) 

 To be continued *********************************************8888 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

##  Filters 

##  Features Features 

##  Key Points 

##  Registration Registration 

##  Kd树Kd-tree 

##  Octree 

##  Segmentation 

 Note: Regarding the learning of point cloud library PCL, you can scan the QR code to follow the official account. If you are interested, you can directly reply to the official account to communicate with me and learn from each other. 

 ![avatar]( 0) 



--------------------------------------------------------------------------------

 The result of the experiment is to run the command, and here you can enter a PCD file at random 

 ![avatar]( 976394-20170308222403453-1583651358.png) 

 You may not see any effect ********************* 

 (2) Image integration 

 Integral image is a method for estimating the discovery of ordered point clouds. The algorithm takes the point cloud as a depth image and creates a certain rectangular area to calculate the normal, taking into account the adjacent pixel relationship without establishing a tree query structure. Therefore, it is very efficient. 

 result visualization 

 ![avatar]( 976394-20170309145925469-432006151.png) 

 See the specific official website pointclouds.org/documentation/tutorials/normal_estimation_using_integral_images.php 

  God, please ignore it!!!! 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303135500376-706958186.jpg) 



--------------------------------------------------------------------------------

 ![avatar]( 976394-20170317010217463-2031530151.png) 

  (2) So how to use PCL to detect pedestrians? Target: detecting people walking on the ground plane Input: RGBXYZ pointcloud ground coeficients Output: people clusters Flowchart: Steps detected on point cloud (1) groud plane estimation and removal (2) Euclidean clustering of remaining points (3) people vertically splitted int more clusters 

 ![avatar]( 976394-20170317010251713-1602906154.png) 

       sub-clustering procedure   (4)candidates pruning based on height from the ground plane   (5) merging of clusters close in groud plane coordinates   (6)Subdivision of big clusters by means of head detection 

      HOG+SVM evaluation   (7)candidate clusters are extened until the ground for achieving robustness to lower limbs occlusion   (8)HOG detector applied to image patches that are projection of 3Dclusters onto the RGB imagepcl::people代码的构架                                   GroundBasedPeopleDetectionAPP<PointT>                                   ________________|_____________________                                   |               |                                                          |                     PersonClassifier<pcl::RGB>   PersonCluster<PointT>   headBasedSubclustering<pointT>                               |                                                  |                         HOG detector                                         HeightMap2D<PointT>  

 code parsing 

  But we know that this requires other header files to cooperate. Then other programs will not be posted one by one. There are also PCL source codes, but if you directly compile it, it cannot be compiled, so we need to write a CMakeLists.txt file to compile. 

 That's it for now... 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303135500376-706958186.jpg) 



--------------------------------------------------------------------------------

 Project code: Simply tested the nearest neighbor search function of k-d tree 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573713657
  ```  
  However, the following error warning appears: 

>  1 > d:\ pcl 1.8.1\ 3rdparty\ flann\ include\ flann\ algorithms\ dist.h (523): error C3861: "pop_t": Identifier not found 1 > d:\ pcl 1.8.1\ 3rdparty\ flann\ include\ flann\ algorithms\ dist.h (523): note: This diagnosis appears in the compiler-generated function "flann :: Hamming Popcnt < T >:: ResultType flann :: Hamming Popcnt < T >:: operator () (Iterator1, Iterator2, size_t, flann :: Hamming Popcnt < T >:: ResultType) const" in 1 > d:\ pcl 1.8.1\ 3rdparty\ flann\ include\ flann\ algorithms\ dist.h (527): note: see Compiling class template instance References to "flann :: Hamming Popcnt < T >" 

#   solution 

 打开pcl 1.8.1\3rdparty\flann\include\flann\algorithms\dist.h文件： 

 The error is located on line 523. 

>  result = lut(reinterpret_cast<const unsigned char*> (a),

                     reinterpret_cast<const unsigned char*> (b), size * sizeof(pop_t)); 

  It turns out that the definition of pop_t data type cannot be found in the current scope. From the above code, copy the relevant definition to the current scope: 

>  typedef unsigned long long pop_t; 

 ![avatar]( 20210524140438600.png) 

  Re-compile, problem solved. 

 ![avatar]( 20210524141518649.png) 



--------------------------------------------------------------------------------

directory 

 One, makeShared: Make the point cloud return a smart pointer (deep copy) 

 二，pcl::visualization::PCLVisualizer 

 viewer.setPointCloudRenderingProperties 

 setPointCloudRenderingProperties()  

 Note 

 III. RenderingProperties 

 Fourth, add text addText, updateText 

 Point cloud segmentation 

 getColoredCloud() 

 Six, experience summary 

#  One, makeShared: Make the point cloud return a smart pointer (deep copy) 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573787270
  ```  
#  二，pcl::visualization::PCLVisualizer 

##  viewer.setPointCloudRenderingProperties 

##  setPointCloudRenderingProperties()  

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573787270
  ```  
 Set the rendering properties of a PointCloud. 

 Parameters 

##  Note 

 Notes: 

 You need to specify the id before setting the property. The default is "cloud". If the id of "cloud" is not set, or other IDs, it will not work. 

 The list of properties can be found in pcl::visualization::LookUpTableRepresentationProperties. 

#  III. RenderingProperties 

 Set of rendering properties. 

#  Fourth, add text addText, updateText 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573787270
  ```  
#  Point cloud segmentation 

##  getColoredCloud() 

 ![avatar]( 20210909145230316.png) 

 If the cloud is successfully split, the function returns a colored cloud. Otherwise a null pointer is returned. Points belonging to the same segment have the same color. But this function does not guarantee that different segments will have different colors (it all depends on the RNG). Points not listed in the indexed array will be indicated in red. 

#  Six, experience summary 

 It is faster to use Release mode in Visual Studio. If it is for running programs rather than debugging, choose Release mode instead of Debug mode. 

 ![avatar]( 20210907114458809.png) 

 ![avatar]( 20210907114438839.png) 



--------------------------------------------------------------------------------

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


--------------------------------------------------------------------------------

 Implementing Registration Algorithms in PCL and Related Concepts 

 Brief Introduction to Pair Registration: The registration problem of a pair of point cloud datasets is pairing registration (pairwise registration or pair-wise registration). Usually by applying an estimated representation of translation and optional 4 * 4 cylinder transformation matrix, a point cloud dataset is accurately registered with another point cloud dataset (target dataset) 

 Specific implementation steps: 

  (1) First, extract key points from both datasets according to the same key point selection criteria 

  (2) Compute the feature descriptors of all selected key points separately 

   (3) Combining the coordinate positions of the feature descriptors in the two datasets, based on the similarity of the features and positions between the two, to estimate their corresponding relationships, and initially estimate the corresponding point pairs. 

 (4) Assuming that the data is noisy, go out to the corresponding point pairs of errors that have an impact on registration 

  (5) Use the remaining correct correspondence to estimate the rigid body transformation, complete registration. 

 Correspondence estimation: Suppose we have obtained two sets of feature vectors obtained from the point cloud data that came to give you this scan. On this basis, we must find similar features and then determine the overlapping parts of the data before we can register. According to the type of feature, PCL uses different methods to search for the correspondence between features 

 When using point matching, the XYZ coordinates of the points are used as feature values, and different processing strategies are used for ordered and unordered point cloud data. 

 (1) Exhaustive registration (brute force matching) 

  (2) kd - Number Nearest Neighbor Query (FLANN) 

 (3) Search in the image space of ordered point cloud data 

   (4) Search in the index space of disordered point cloud data 

 (3) Removal of correspondence (correspondence rejection) 

 Due to the influence of noise, usually not all the estimated correspondence relationships are correct. Since the wrong correspondence relationship will have a negative impact on the estimation of the final rigid body transformation matrix, they must be removed. Random sampling consistency estimation can be used, or other methods can be used to eliminate the wrong correspondence relationship. Finally, only a certain proportion of the correspondence relationship is used for the number of correspondence relationships, which can not only improve the estimation of the transformation matrix, but also improve the speed of the registration point. 

 (4) Estimation of the transformation matrix (transormation estimation) 

 The steps to estimate the correspondence matrix are as follows 

   1. Evaluate some wrong metrics on the basis of correspondence 

  2. Estimate a rigid body transformation with camera pose (motion estimation) and minimized error metrics 

  3. Structure of optimization points 

  4 Use rigid body transformation to rotate/translate the source to the same coordinate system as the target, and use all points, a subset of points, or key points to calculate an internal ICP loop 

  5. Iterate until the convergence criterion is met. 

  (5) Iterative closest point algorithm (ICP algorithm for short) 

 The ICP algorithm treats the spliced two point clouds, first establishes the corresponding point sets P and Q according to certain criteria, and then calculates the optimal coordinate transformation through the minimum multiplication iteration, that is, the rotation matrix R and the translation vector t, so that the error function is minimized. The ICP processing flow is divided into four main steps: 

   1. Sample the original point cloud data 

  2. Determine the initial set of corresponding points 

  3. Remove the error corresponding point pair 

  4. Solution of coordinate transformation 

 ![avatar]( 976394-20170309230916828-653469568.jpg) 

 Introduction to PCL classes 

 Example analysis: 

 (1) How to use the iterative closest point algorithm: using the ICP iterative closest point algorithm in the code, the program randomly generates a point and as the source point cloud, and translates it along the x-axis as the target point cloud, and then uses the ICP to estimate the source-to-target rigid body transform orange, and prints all the information in the middle 

 New file 

 iterative_closest_point.cpp 

 The result of compiling and running 

 ![avatar]( 976394-20170302144402657-1675036526.png) 

 It can be seen from the experimental results that the transformed point cloud only increases the value of the x-axis by a fixed value of 0.7, and then its rotation and translation are calculated from the target point cloud and the source point cloud. It is obvious that the x value of the last row is 0.7. 

 Also, we can modify the program ourselves to observe different experimental results. 

 For two images, find its transformation through ICP: 

 At first, if you directly get the data through kinect, the following error will occur because the ICP algorithm cannot handle point cloud data containing NaNs, so you need to remove these points before they can be used as input to the ICP algorithm 

 Wrong prompt 

 ![avatar]( 976394-20170310000432797-1352400041.png) 

 Therefore, we must remove the invalid point cloud through the code we learned before, and then use it as input. Since I obtained the point cloud data myself, the data is not preprocessed. The result of the input two point clouds after ICP is visualized as 

 ![avatar]( 976394-20170310002016641-634666106.png) 

 ![avatar]( 976394-20170310001934109-475953061.png) 

 (2) How to gradually match multiple point clouds 

 This example uses the iterative closest point algorithm to gradually achieve a pair-by-pair match for a series of point clouds. His idea is to transform all point clouds so that they are all in a unified coordinate system with the first point cloud. Find the best transformation between each coherent overlapping point cloud, and accumulate these transformations to all point clouds. Point clouds capable of performing ICP algorithms require rough pre-matching (such as within the distance of a robot or within the frame of a map), and one point cloud needs to overlap with another point cloud. 

 New file pairwise_incremental_registration cpp 

 Run the executable file 

  ./pairwise_incremental_registration frame_00000.pcd capture0001.pcd capture0002.pcd capture0004.pcd capture0005.pcd 

 ![avatar]( 976394-20170315103341323-1522754095.png) 

 ![avatar]( 976394-20170315103757916-1486384013.png) 

  If you can't see the result, press R to reset the camera. Adjusting the angle can observe that there are two groups of red and green point clouds displayed on the left side of the window, and red is the source point cloud. You will see similar results above. The command line prompts that you need to perform registration. Press Q, and after pressing, you can find that the window on the left continuously adjusts the point cloud. In fact, it is the output of the intermediate result of the iteration in the registration process. Before the number of iterations is less than the set number of times, the right side will continuously refresh the latest registration result until it converges. The number of iterations is 30 times to complete the entire matching process. After pressing Q again, you will see the stored 1.pcd file. This file is the point cloud under the same coordinate system as the first input point cloud after the first and second point clouds are registered. 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303135538079-444707830.jpg) 

 To be continued ************************************8 



--------------------------------------------------------------------------------

 Introduce how to use the normal distribution algorithm to determine the rigid body transformation between two large point clouds. The normal distribution transformation algorithm is a registration algorithm, which is applied to the statistical model of three-dimensional points. Standard optimization techniques are used to determine the optimal match between two point clouds. Because it does not use the characteristic calculation and matching of the corresponding point in the registration process, the time is faster than other methods. 

 Parsing of the code 

 The result of compiling and running: 

 ![avatar]( 976394-20170315135631354-999762274.png) 

 ![avatar]( 976394-20170315135620010-1432698624.png) 

 (2) This experiment will learn how to write an interactive ICP visualization program. The program will load the point cloud and perform a rigid transformation on it. After that, use the ICP algorithm to align the transformed point cloud with the original point cloud. Each time the user presses "space", ICP iteration is performed, and the visualization interface is refreshed. 

 Here the original routine uses a PLY format file, you can find a PLY format file for experimentation, or you can use the format conversion file to convert the PCD file into a PLY file 

 After generating the executable file 

 ![avatar]( 976394-20170320141557299-188372473.png) 

                                        Basic information for window output 

 ![avatar]( 976394-20170320141602580-986757512.png) 

                                                     Just started iterating the first result 

 ![avatar]( 976394-20170320141611268-342218778.png) 

                                                                Press the space bar to iterate over the result 

 Done, if there is any error, please contact me to communicate, thank you, Daniel, please ignore it. 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303135500376-706958186.jpg) 



--------------------------------------------------------------------------------

(1) About the registration of the point cloud 1. First give the source point cloud and the target point cloud. 2. Extract features to determine the corresponding point 3. Estimate the transformation matrix corresponding to the matching point 4. Apply the transformation matrix to the source point cloud to the target point cloud 

 ![avatar]( 20191220193315354.png) 

  Flowchart of registration, through the matching steps of feature points 

 ![avatar]( 20191220193352440.png) 

 (1) Compute the key points of the source point cloud and the target point cloud (2) Compute the feature descriptors of the key points (such as FPFH, etc.) (3) Match the feature points to calculate the correspondence (4) Estimate the transformation matrix from the correspondence between the feature points, which is the same as the principle of using feature points such as harris corners to calculate the transformation matrix between two images in Opencv, so the ideas and workflow of the algorithms used are also very similar 

 ![avatar]( 20191220193432428.png) 

 There are many ways to calculate the transformation matrix T = (R, t), if the paired points (Di, Mi) are given: (1) point-to-point (2) point-to-plane (3) plane-to-plane pairing, etc., the method of minimizing the minimum distance from point to point based on SVD decomposition (the formula for the minimum variance error): then there will definitely be false matches, and the method of removing the false matching points (outliers) uses the RANSAC method 

 ![avatar]( 2019122019345612.png) 

 (1) Find three pairs of corresponding matching points (Di, Mi) (2) Estimate the transformation matrix (R, t) based on these points (3) For matching points, set a certain condition as the inner point (4) Repeat the above steps N times until (R, t) has many inner points, and the initial match (you can see a lot of false matches) * The match calculated by the RANSAC algorithm * 

 ![avatar]( 20191220193641825.png) 

 ![avatar]( 20191220193728791.png) 

 ![avatar]( 20191220193743407.png) 

 After finding the transformation matrix between the feature points, we want to completely correspond to the source point cloud and the target point cloud and use the ICP algorithm. As shown in the figure, we think that M is used as the model setting point, and S is used as the corresponding scene. We think that every point on S has a corresponding point on M. If we know the correct registration point, we can find the rotation and translation between the two. So what if we find a registration with the smallest error? We need to use the ICP algorithm. The algorithm flow and pseudo-code of the algorithm are as follows: If there are any errors in the above content or need to be added, please leave a message! At the same time, everyone is welcome to pay attention to the WeChat official account, actively share the submissions, and share them together. Refuse to be just a reaching party! Or join the 3D visual WeChat group or QQ communication group to communicate and share together! 

 Submit or contact the group owner Email: dianyunpcl@163.com 

 ![avatar]( 20191220193903497.png) 

 Original is not easy, please contact the group owner for reprinting and indicate the source.  



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

The segmentation of the point cloud is a very important part of the robotic arm capture I want to do, so first learn how to use the point cloud library to process the point cloud data I get with kinect. This routine is also my own slow modification program and combined with the explanation of the official API. There are many details. If you change the source program directly, it may be compiled for various reasons such as data type or header files. However, it will be more difficult for us to find out the errors. First, let's take a look at a scene I set myself, and then I use kinect to get the data 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3MDUzNjk3MS04MDQ0MjUyNTQucG5n) 

 Observe the original image acquired by kinect, and then use a simple filter to remove the NANS points in it, because many algorithms require that NANS points cannot appear. We can see that there are power banks, ink, ping pong balls, a pair of chopsticks, and two pieces of paper below. Two pieces of black tape are pasted on them. We can first do an experiment to extract the plane of the original point cloud. If we extract the plane in the point cloud, there are some basic examples before, using the plane segmentation method 

 The procedure is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573781028
  ```  
 Running the generated executable will output the parameters of the plane model 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3MjMxNzY5MC0yMjYzMzA0NTgucG5n) 

                                                                Parameters of the plane model 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3MjMwODA4MC04NTI2MTk3MjkucG5n) 

                                                                       This is a cloud of sampled points. 

 It is also possible to directly implement plane extraction in this program, but for better illustration, I will divide the acquisition of plane parameters and plane extraction into two programs. The program is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573781028
  ```  
 The execution result is as follows 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3NTIxMjM2MS0xNzM2MjE1NzA0LnBuZw) 

 Extracting the plane, **********************8 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzEzNTUwMDM3Ni03MDY5NTgxODYuanBn) 



--------------------------------------------------------------------------------

 (1) Smoothing the point cloud with the least squares method 

 New file resampling.cpp 

 result comparison 

 ![avatar]( 976394-20170303163421282-362220584.png) 

 (2) Extracting convex (concave) polygons from plane models 

 This example first extracts the plane model from the point cloud, then projects a set of points from the filtered point cloud to form a point cloud through the estimated plane model coefficients, and finally calculates the corresponding two-dimensional convex polygon for the projected point cloud 

 Experimental results 

 ![avatar]( 976394-20170303170408141-2093172829.png) 

  (3) Rapid triangulation of disordered point clouds 

 The directed point cloud is triangulated using the greedy projection triangulation algorithm. 

 The specific methods are: 

 (1) First project a directed point cloud into a local two-dimensional coordinate plane 

 (2) Perform in-plane triangulation in the coordinate plane 

 (3) Obtain a triangular mesh surface model according to the topological connection relationship of three points in the plane. 

 Principle of Greedy Projection Triangulation Algorithm: 

 It is to process a series of points (edge points) that can "grow and expand" the mesh, extending these points until all points that meet the geometric and topological correctness are connected, but the algorithm also has great limitations, it is more suitable for sampling point clouds from continuous smooth surfaces and the density change of point clouds is relatively uniform 

  First, take a look at the original PCD visualization file 

 ![avatar]( 976394-20170322115940361-132256953.png) 

 The result of triangulating and visualizing it is 

 ![avatar]( 976394-20170322120009315-1385092394.png) 

 The effect is still obvious 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( 976394-20170303135500376-706958186.jpg) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

 (1) Introduction to RANSAC Random Sampling Consistency Algorithm 

 RANSAC stands for "random sample consensus". It estimates the parameters of a mathematical model iteratively from a dataset of observations containing "outliers". It is indeterminate - it has a reasonable probability of arriving at a reasonable result; the number of iterations must be increased to increase the probability. 

 There are two types of data: valid data (inliers) and invalid data (outliers). Data with little deviation is called valid data, and data with large deviation is invalid data. If the valid data is the majority and the invalid data is only a small amount, we can determine the parameters and errors of the model through least squares or similar methods; if there is a lot of invalid data (for example, more than 50% of the data is invalid data), the least squares method will fail, and we need new algorithms 

 A simple example is to find a suitable 2-dimensional line from a set of observations. Suppose the observations contain both inside and outside points, where the inside points are approximately passed by the line, and the outside points are far from the line. Simple least squares cannot find a line that fits the inside points, because the least squares method tries to fit all points, including the outside points. In contrast, RANSAC can come up with a model calculated using only the inside points, and the probability is high enough. However, RANSAC cannot guarantee that the result will be correct. To ensure that the algorithm has a high enough reasonable probability, we must choose the parameters of the algorithm carefully. 

 ![avatar]( 976394-20170227230942001-1056345374.png) 

                                    Left: a dataset with many outliers, right: a straight line found by RANSAC (outliers do not affect the results) 

 (2) Minimum Median Value Method (LMedS) 

 The approach of LMedS is very simple, that is, randomly extract N sample subsets from the sample, use the maximum likelihood (usually least squares) to calculate the model parameters and the deviation of the model for each subset, record the model parameters and the deviation of the sample with the median deviation in all the samples in the subset (i.e. Med deviation), and finally select the corresponding model parameters with the smallest Med deviation in the N sample subsets as the model parameters we want to estimate. 

 Geometry models supported by sample_consensus module in PCL 

 (2) Introduction of Sample_consensus modules and classes in PCL 

 The Sample_consensus library in PCL realizes random sampling consistency and its generalization estimation algorithm, such as plane, cylinder, and other common geometric models, using different estimation algorithms and different geometric models to freely combine to estimate the coefficients of specific geometric models implied in point clouds, and realize the segmentation of geometric models located in point clouds. Lines, planes, cylinders, and spheres can all be realized in the PCL library. Planar models are often used in the segmentation extraction of common indoor planes, such as walls, floors, desktops. Other models are often applied to detect, identify and segment objects according to geometric structures. They can be divided into two categories: one is the implementation of sampling consistency and its generalization function, and the other is the specific implementation of several different models, such as: planes, lines, spheres, etc 

 It is the base class of different model implementations in the random sampling consistency estimation algorithm. All sampling consistency estimation models inherit from this class. The related general interface of the sampling consistency model is defined. The specific implementation is completed by the subclass, and its inheritance relationship: 

 ![avatar]( 976394-20170227234328251-744674086.png) 

 Introduction of class members 

 (2) is the base class of sampling consistency algorithms 

 （3） 

 Code Example random_sample_consensus cpp 

 Run result: 

 In the absence of any parameters, the three-dimensional window displays the original point cloud created (containing both internal and external points), as shown in the figure. It is obvious that this is a diamond-shaped plane with noise, and the noise points are cubes. If we are generating a point cloud, we are generating random numbers in the range (0, 1). 

 ./random_sample_consensus 

 ![avatar]( 976394-20170228153338407-497233380.png) 

 ./random_sample_consensus -f 

 ![avatar]( 976394-20170228153431157-410722979.png) 

 ./random_sample_consensus -sf 

 ![avatar]( 976394-20170228153452016-708414723.png) 

  To be continued ****************************************************8 



--------------------------------------------------------------------------------

