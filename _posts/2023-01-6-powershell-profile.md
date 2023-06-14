---
layout: posts
title: Powershell start script
date: 2023-01-06
categories: powershell shell 
---

# Powershell에서 프로파일 등록 하기

bash에서 .bashrc를 사용 하여 변수 등롤 및 셀 환경 설정을 기능 처럼 윈도우 파워쉘에서도 시작 스크립트를 작성 가능 합니다.

## $로 변수 사용

```bash
cd $PSHOME
```

$PSHOME이 변수는 파워쉘이 설치되어 있는 경로입니다.

이 경로에 파워쉘 스크립트를 작성 할수 있습니다.

```bash
cd $PSHOME
nvim Profile.ps1
```

파워쉘이 설치 되어있는 폴더에 Profile.ps1을 추가 합니다.

이 Profile.ps1에 파워쉘 스크립을 작성 하면 됩니다.
