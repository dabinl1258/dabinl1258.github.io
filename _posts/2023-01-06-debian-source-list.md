---
layout: posts
title: Change Debian Apt Server
date: 2023-01-06
categories: linux debian
---

# 데비안 Apt 저장소 변경

데비안은 패키지 매니저로 Apt를 사용 합니다.

또한 기본 저장소의 위치는 해외에 있습니다.

기본 서버가 해외에 있기 때문에 속도가 느림니다.

``'bash
/etc/apt/sources.list

```
서버의 위치는 /etc/apt/sources.list에서 설정합니다.

/etc/apt/sources.list를 vim으로 열고 아래를 입력 합니다.

```bash
:%s/deb.debian.org/ftp.kaist.ac.kr/
:%s/security.debian.org/ftp.kaist.ac.kr/
```
