 Project code: Simply tested the nearest neighbor search function of k-d tree 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309573713657
  ```  
  However, the following error warning appears: 

>  1 > d:\ pcl 1.8.1\ 3rdparty\ flann\ include\ flann\ algorithms\ dist.h (523): error C3861: "pop_t": Identifier not found 1 > d:\ pcl 1.8.1\ 3rdparty\ flann\ include\ flann\ algorithms\ dist.h (523): note: This diagnosis appears in the compiler-generated function "flann :: Hamming Popcnt < T >:: ResultType flann :: Hamming Popcnt < T >:: operator () (Iterator1, Iterator2, size_t, flann :: Hamming Popcnt < T >:: ResultType) const" in 1 > d:\ pcl 1.8.1\ 3rdparty\ flann\ include\ flann\ algorithms\ dist.h (527): note: see Compiling class template instance References to "flann :: Hamming Popcnt < T >" 

#   solution 

 打开pcl 1.8.1\3rdparty\flann\include\flann\algorithms\dist.h文件： 

 The error is located on line 523. 

>  result = lut(reinterpret_cast<const unsigned char*> (a),

                     reinterpret_cast<const unsigned char*> (b), size * sizeof(pop_t)); 

  It turns out that the definition of pop_t data type cannot be found in the current scope. From the above code, copy the relevant definition to the current scope: 

>  typedef unsigned long long pop_t; 

 ![avatar]( 20210524140438600.png) 

  Re-compile, problem solved. 

 ![avatar]( 20210524141518649.png) 

