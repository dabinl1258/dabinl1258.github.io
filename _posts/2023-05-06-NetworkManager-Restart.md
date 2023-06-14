---
layout: posts
title: NetworkManager Restart
date: 2023-05-06 09:00:00
categories: arch linux system
---

```bash
sudo systemctl restart NetworkManager.service 
```

위 명령어는 NetwrokManager.service를 재시작 한다.

씽크패드 x230에 아치 리눅스를 설치 하였는데 tlp(전력 관리)프로그램과 충돌로 가끔 wifi가 꺼진다.
tlp옵션에서 설정을 해보았지만 역시 해결 되지 않는다. 이때 이방법으로 해결을 하였다.
