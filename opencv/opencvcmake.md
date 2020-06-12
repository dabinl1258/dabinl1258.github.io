# OpenCv with cmake 



* projectname
    * test.cpp
    * cmakelists.txt
    * test.jpg

```c++
/* 
    projectname/test.cpp
*/
#include <opencv2/highgui.hpp>

int main()
{
	cv::Mat img = cv::imread("test.jpg");
	cv::namedWindow("test.jpg", cv::WINDOW_AUTOSIZE);
	cv::imshow("test.jpg", img);
	cv::waitKey(0);
	return 0;
}
```

```cmake
##  projectname/cmakelists.txt
cmake_minimum_required(VERSION 3.0)
project( projectname )
find_package( OpenCV REQUIRED ) # opencv 페키지를 검색 
include_directories(${OpenCV_INCLUDE_DIRS}  ) # include 디렉토리 추가 
add_executable( projectname test.cpp )
target_link_libraries(projectname ${OpenCV_LIBS}) # 프로젝트에 opencv를 링킹

```

usually
```shell
$mkdir build 
$cd build
$cmake ../
$make 

```

then

* projectname
    * test.cpp
    * cmakelists.txt
    * test.jpg
    * build
        * make 
        * projectname #생성된 실행 파일 

* 보통 파일등의 리소스를 실행파일 위치에서 로드 하기 때문에 실행파일 위치에 리소스 이동

```shell 
 projectname$ mv test.jpg build/test.jpg
```

## result 
![alt text](result.jpg)

