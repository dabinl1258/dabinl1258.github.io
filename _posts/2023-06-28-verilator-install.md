---
layout: posts
title: verilator 설치  
date: 2023-06-28 00:00:00
categories: verilog systemC c++ cmake ninja
---

verilator는 SystemVerilog를 시뮬레이션 하기 위한 소프트웨어다.

verilotor를 설치하는 방법에는 2가지가 있다.

1. apt등 패키지 매니저를 이용한설치

2. 직접 코드를 컴파일

이중에서 apt등 패키지 매니저를 이용한 설치의 경우 설치 되는 버전에 제약이 따른다. 그럼으로 이 포스트에서는 직접 코드를 컴파일 하는 방법에 대해서 기술 하겠다.

직접 코드를 이용해서 컴파일 하는 방법에는 make빌드를 하는 방법과 cmake 빌드를 하는 방법으로 나뉜다. make빌드의 경우 느리기 때문에 cmake와 ninja를 이용한 빌드 방법에 대해서 기술을 하겠다.

## build 준비물

* python

* cmake

* git

* llvm clang or MSVC

* flex

* bison

* ninja-build

우분투의 경우 다음의 명령어로 설치가 가능하다.

```bash
sudo apt install help2man python3 cmake llvm clang git flex bison ninja-build -y
```

저장소로 부터 소스코드 가져오기

```bash
git clone https://github.com/verilator/verilator
cd verilator 
```

빌드 

 

```bash
mkdir build
cd build
cmake .. -G Ninja # 닌자로 빌드
cmake --build . --config Release # ninja
```

설치 

`VERILATOR_ROOT' 환경 변수 설정후 아래 커맨드를 입력한다.

```
cmake --install .
```

단 지금 현재 cmake 빌드의 경우 


