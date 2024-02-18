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

