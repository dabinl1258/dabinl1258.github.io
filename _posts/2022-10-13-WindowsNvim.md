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

init.vim에 다음 내용을 추가 한다.
```
call plug#begin()

call plug#end()
```
이제 추가한 내용사이에 설치할 플러그인을 넣고 나서 vim에서 PlugInstall명령어를 사용하면 된다.

## 자동완성을 위한 coc설치 및 세팅

coc를 설치하기에 앞서 nodejs가 설치 되어 있어야 한다.

### coc plugin 설치


```bash
Plug 'neoclide/coc.nvim', {'branch': 'release'}
```
vim-plug를 사용해서 coc를 설치한다.

### coc에서 tab complete사용 
tab키를 이용해서 자동 완성을 하기 위해서 init.nvim에 다음을 추가 한다.

```
inoremap <silent><expr> <tab> pumvisible() ? coc#_select_confirm() : "\<C-g>u\<TAB>"
```

