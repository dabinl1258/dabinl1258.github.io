---
layout: posts
title: GCC -I Option
date: 2023-08-21
tags : [digital, uart, protocol ]
---
GCC option -I는 Include의 약자로 Include 즉  *.h 파일이 모여 있는 위치 또는 *.h파일의 경로를 입력 합니다.


Header 파일의 위치를 다른 곳으로 두기 위해서 사용합니다.
```bash
gcc -o hello -I <header Directory Path >
```