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

