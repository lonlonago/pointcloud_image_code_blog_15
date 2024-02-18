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

