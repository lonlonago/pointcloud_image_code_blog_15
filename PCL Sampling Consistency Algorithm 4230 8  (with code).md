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

