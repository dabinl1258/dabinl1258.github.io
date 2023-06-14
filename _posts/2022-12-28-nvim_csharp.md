---
layout: posts
title: nvim csharp
date: 2022-12-28
categories: nvim vim c#
---

#nvim에 c# 세팅
nvim에 c# lsp를 세팅하는 과정을 알아본다.

## 준비물

* C#런타임
* dotnet cli
* ms build tools .net (linux의 경우 mono) 
  
  ## C# lsp서버 설치
  
  dotnet 명령어를 이용하여 c# lsp인 csharp-ls를 설치 한다.
  
  ```bash
  dotnet tool install --global csharp-ls
  ```

### OmniSharp 설치

vim-plug를 통해서 OmniSharp-vim을 설치한다.

```
Plug 'OmniSharp/omnisharp-vim'
```

vim을 열고 다음을 입력해서 OmniSharp를 설치한다.

```
:OmniSharpInstall
```
