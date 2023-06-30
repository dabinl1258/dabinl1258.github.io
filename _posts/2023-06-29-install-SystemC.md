```yaml
layout: posts
title: SystemC 설치
date: 2023-06-29 00:00:00
categories: verilog systemC c++ make
```

SystemC 설치하는 법

github에서 저장소를 clone하고 해당 폴더로 간다.

```bash
git clone https://github.com/accellera-official/systemc
cd systemc
```

버전을 checkout 받는다.

```bash
git checkout 2.3.4
```

빌드전 Prerequisites를 받는다.

```bash
sudo apt install cmake ninja-build clang make pkg-config build-essential -y 
```

build를 폴더 생성 및 이동 한다.

```bash
mkdir build
cd build
```

cmake를 실행한다.

```bash
cmake .. -G Ninja
cmake --build .
sudo cmake --install .
```

환경 변수를 세팅한다.

```bash
export SYSTEMC_INCLUDE=/opt/systemc/include
export SYSTEMC_LIBDIR=/opt/systemc/lib
export SYSTEMC=/opt/systemc
```


