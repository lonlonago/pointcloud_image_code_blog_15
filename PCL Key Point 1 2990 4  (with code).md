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

