-
layout: posts
title: Jekyll 
data: 2022-10-13
categories: nvim
---
# Windows에서의 nvim vimrc 위치
Windows에서는 ~/AppData/Local/init.vim파일을 수정해 주면 된다.

## vim-plug 설치
[vim-plug github](https://github.com/junegunn/vim-plug) 


윈도우에서는 vim plugin을 설치 하기 위해서 vim-plug를 설치한다.
```bash
iwr -useb https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim |`
    ni $HOME/vimfiles/autoload/plug.vim -Force
```

