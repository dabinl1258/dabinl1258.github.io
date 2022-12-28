---
layout: posts
title: nvim csharp
data: 2022-12-28
categories: custom pls
---

#nvim에 c# 세팅
nvim에 c# lsp를 세팅하는 과정을 알아본다.

## 준비물
* C#런타임
* dotnet cli
* coc가 세팅된 nvim

## C# lsp서버 설치 
dotnet 명령어를 이용하여 c# lsp인 csharp-ls를 설치 한다.
```bash
dotnet tool install --global csharp-ls
```

vim에서 CocConfig를 이용해 CocConfig파일을 연다. 아래 내용을 추가한다.
```
{
    "languageserver": {
        "csharp-ls": {
          "command": "csharp-ls",
          "filetypes": ["cs"],
          "rootPatterns": ["*.csproj", ".vim/", ".git/", ".hg/"]
        }
    }
}
```
