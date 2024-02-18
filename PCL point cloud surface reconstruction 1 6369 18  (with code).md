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

