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

