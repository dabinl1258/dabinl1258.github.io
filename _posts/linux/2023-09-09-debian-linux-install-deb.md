---
layout: posts
title: 데비안 계열 리눅스 deb 파일 설치
date: 2023-09-09 
tag: [install, debian, linux]
---
데비안 계열 os에서는 *.deb(debian software package)라는 패키지를 사용한다. 이를 설치하기 위해서는 dpkg 명령어를 이용한다.

dpkg -i or --install 옵션을 이용해서 패키지를 설치한다.
```bash
dpkg -i <package file name> 
```