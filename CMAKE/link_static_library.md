# link static library 

이전에 만든 libhellowolrd.a를 링크해서 Hello함수를 호출 해보겠습니다.

- hellworld 
    - CMakeLists.txt
    - main.cpp
    - helloworld.h 
    - libhelloworld.a

hellowolrd.h와 libhelloworld.a는 이전 글에서 만들거를 복사해 주세요

```cmake
#hellworld/CMakeLists.txt
cmake_minimum_required (VERSION 2.8)
project(helloworld)
add_executable(helloworld main.cpp)
target_link_libraries(helloworld ${CMAKE_SOURCE_DIR}/libhelloworld.a) // 소스 디렉토리의 libhelloworld.a를 링크 
```

```cmake
${CMAKE_SOURCE_DIR} 소스 디렉토리 


```c
#include "helloworld_lib.h"
int main()
{
    Hello();
    return 0;
}
```

```shell
$mkdir build 
$cd build 
build $ cmake ../
build $ make 
build $./helloworld
helloworld
````
다음과 같이 결과를 볼수 있다.