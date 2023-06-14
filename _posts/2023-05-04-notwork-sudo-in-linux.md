---
layout: posts
title: 리눅스에서 sudo가 안될때 해결 법
date: 2023-05-04 00:09:00
categories: termux linux
---

간혹 리눅스에서 sudo를 치고 password를 입력 해도 sudoer를 확인해 
보라는 안내메시지만 뜨고 sudo 명령어를 통해서 root에서 사용을 못할 떄가 있다.
이런 경우는 현제 세션의 user가 추가된 그룹이 /etc/sudoers에서 sudo명령어를 사용할 권한이 없어서 그렇다.

따라서 /etc/sudoers를 편집하여 해결 하면 된다. 
일반 적으로 앞에 ALL 대신 하여 그룹명을 써야 하지만 TERMUX 문제인지 필자는 이렇게 해결 하였다.

```bash
ALL ALL=(ALL:ALL) ALL 
```
