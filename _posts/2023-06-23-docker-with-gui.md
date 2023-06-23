---

layout: posts
title: Docker gui같이 쓰기
date: 2023-06-23 23:19:00
categories:  docker log gui
---



## 목적

docker image로 부터 cotainer를 만들고 xming을 이용해 gui를 공유 한다.

## 준비물

docker가 설치된 os

xming 설치후 DISPLAY 변수를 등록



## 발견한 문제점

docker를 설치 하는 경우에 snap에서 제공하는 버전을 설치한 경우 gui를 사용이 불가능 하다.





## 옵션

```shell
docker container create -v /tmp/.X11-unix:/tmp/.X11-unix:ro -e DISPLAY=${DISPLAY}
```

위 옵션을 넣어서 도커 컨테이너를 생성한다.





참고 : 

[docker에서 컨테이너 gui 실행하기](https://conservative-vector.tistory.com/entry/docker%EC%97%90%EC%84%9C-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88-gui-%EC%8B%A4%ED%96%89%ED%95%98%EA%B8%B0)
