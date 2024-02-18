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

