```
layout: posts
title: verilator make 빌드  
date: 2023-06-29 00:00:00
categories: verilog systemC c++ make verilator
```

verilator 빌드와 설치에 대한 방법이다.

다음 명령어를 통해서  Prerequisites를 설치한다.

```bash
sudo apt-get install git help2man perl gdb python3 make autoconf g++ flex bison ccache -y
sudo apt-get install libgoogle-perftools-dev numactl perl-doc -y
sudo apt-get install libfl2  -y # Ubuntu only (ignore if gives error)
sudo apt-get install libfl-dev  -y# Ubuntu only (ignore if gives error)
sudo apt-get install zlibc zlib1g zlib1g-dev -y  # Ubuntu only (ignore if gives error)
```

git명령어를 통해서 소스코드를 다운 받고 그 폴더로 이동한다.

```bash
git clone https://github.com/verilator/verilator 
cd verilator
```

혹시 모를 환경 변수를 삭제한다.

```bash
unset VERILATOR_ROOT
```

autoconf로 configure스크립트를 생성한다.

```bash
autoconf 
```

configure 스크립트를 실행한다.

```bash
./configure
```

build를 진행한다. -j  $(nproc)은 멀티코어를 100% 활용하는 옵션이다.

CXXFLAGS='-std=c++17'은 c++17버전으로 컴파일 하는 욥션이다.

```bash
make -j `nproc` CXXFLAGS='-std=c++17'
```

설치 한다.

```bash
make install 
```
