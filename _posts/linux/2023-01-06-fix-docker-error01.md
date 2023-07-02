---
layout: posts
title: docker  Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?.
date: 2023-01-06
categories: docker linux debian
---

# docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?.

docker: Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?.이 에러는 도커 서비스가 실행 되지 않아서 생기는 문제 입니다. 

```bash
sudo systemctl start docker
```

위 명령을 이용해서 도커 서비스를 다시 실행해 주면 됩니다.
