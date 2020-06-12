# Make hello world with CMake 

- project_name 
    - CMakeLists.txt
    - main.c 

```c
/* project_name/main.c
*/
#include <stdio.h>

int main()
{
    printf("hello world!\n");
    return 0;
}

```

```cmake
# project_name/CMakeLists.txt
cmake_minimum_required ( VERSION 2.6) # cmake 최소 버전확인 
project(project_name) # 프로젝트 이름 설정 
add_executable(project_name main.c) # 소스코드 추가
```

```console 
$mkdir build 
$cd build
$cmake ../ # 상위 디렉토리를 지정 CMakeLists.txt가 현재 디렉토리에 있는 경우에는 생략가능 
$make  # cmake로 부터 생성된 Makefile을 이용하여 컴파일 
$./project_name # 실행
hello world!
```

