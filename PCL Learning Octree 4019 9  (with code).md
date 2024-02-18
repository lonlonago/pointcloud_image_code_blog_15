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

