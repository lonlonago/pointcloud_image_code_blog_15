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

