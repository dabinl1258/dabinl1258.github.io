---
layout: posts
title: Jeykll 블로그 글쓰는 법 
date: 2023-05-06 00:01:30
categories: jekyll
---

jekyll에 post를 쓰는 방법은 _posts경로 아래에 글을 쓰는 방법이 있다.

이때 markdown파일명은 다음과 같은 규칙을 가진다.

1. yyyy-mm-dd-name.md 

2. 파일명에는 '_'가 들어 갈수 없다.
   ex) 
   
   2033-03-01-new_post.md // not allow
   2033-03-01-new-post.md // allow

post파일의 경우 상단에 다음과 같은 속성이 위치 한다.

```
---
layout: posts
title: 재목
date: yyyy-mm-dd hh:mm:ss
cartegories: tag1 tag2
---
```

1. layout , _layouts에 정의 되어 있는 posts
2. title, post의 제목
3. date post가 작성된 날짜 뒤에 있는 시분초 utc는 생략 가능 하다. 위 경우에는 utc+9이다
4. cartegories, 공백으로 구분된 카테고리 assets/img/
