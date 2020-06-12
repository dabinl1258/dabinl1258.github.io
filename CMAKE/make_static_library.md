# make static library 

- helloworld_lib
    - CMakeLists.txt
    - helloworld.h
    - helloworld.cpp

```c 
/*
helloworld_lib/helloworld.h
*/
#include <stdio.h>
void Hello();
```

```c

/*
helloworld_lib/helloworld.h
*/
#include "helloworld.h"

void Hello()
{
    printf("hello world\n");
}
```

```cmake 
#helloworld_lib/CMakeLists.txt
cmake_minimum_required (VERSION 2.8)
add_library(helloworld helloworld_lib.cpp helloworld_lib.h) # 앞에 hellworld가 static lib 이름 
```

usally 

```shell 
$mkdir build 
$cd build 
build$cmake ../
build$make 
```

- helloworld_lib
    - CMakeLists.txt
    - helloworld.h
    - helloworld.cpp
    - build
        - libhelloworld.a 
libhelloworld.a가 생성됨 

주의 할 점은 라이브러리 이름 앞에 lib 붙습니다.

그다음 에는 static lib를 링크 하는 법에 대해서 알아 보겠습니다.


[link static library](link_static_library)