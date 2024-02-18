The segmentation of the point cloud is a very important part of the robotic arm capture I want to do, so first learn how to use the point cloud library to process the point cloud data I get with kinect. This routine is also my own slow modification program and combined with the explanation of the official API. There are many details. If you change the source program directly, it may be compiled for various reasons such as data type or header files. However, it will be more difficult for us to find out the errors. First, let's take a look at a scene I set myself, and then I use kinect to get the data 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3MDUzNjk3MS04MDQ0MjUyNTQucG5n) 

 Observe the original image acquired by kinect, and then use a simple filter to remove the NANS points in it, because many algorithms require that NANS points cannot appear. We can see that there are power banks, ink, ping pong balls, a pair of chopsticks, and two pieces of paper below. Two pieces of black tape are pasted on them. We can first do an experiment to extract the plane of the original point cloud. If we extract the plane in the point cloud, there are some basic examples before, using the plane segmentation method 

 The procedure is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573781028
  ```  
 Running the generated executable will output the parameters of the plane model 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3MjMxNzY5MC0yMjYzMzA0NTgucG5n) 

                                                                Parameters of the plane model 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3MjMwODA4MC04NTI2MTk3MjkucG5n) 

                                                                       This is a cloud of sampled points. 

 It is also possible to directly implement plane extraction in this program, but for better illustration, I will divide the acquisition of plane parameters and plane extraction into two programs. The program is as follows 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573781028
  ```  
 The execution result is as follows 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMyMTE3NTIxMjM2MS0xNzM2MjE1NzA0LnBuZw) 

 Extracting the plane, **********************8 

 WeChat official account number can scan the QR code to learn and communicate together 

 ![avatar]( aHR0cDovL2ltYWdlczIwMTUuY25ibG9ncy5jb20vYmxvZy85NzYzOTQvMjAxNzAzLzk3NjM5NC0yMDE3MDMwMzEzNTUwMDM3Ni03MDY5NTgxODYuanBn) 

