---
layout: single
title: "블로그 좌우 여백이 너무 넓다"
categories: ['Github Pages']
tags: ['github pages']
permalink : /GithubPages/4
---

> 이 글은 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)를 기준으로 작성되었다.

본문이 차지하는 공간에 비해 좌우 여백이 너무 넓다고 느꼈다.

검색 결과 [Padomay님의 블로그](https://padomay-dev.github.io/jekyll/jekyll-sidebar-edit/)를 참고하여 작업했다.

`_sass\minimal-mistakes\_variables.scss` 파일에서 `Grid` 부분에 `right-sidebar` 넓이를 `30px` 씩 줄인다. 

이름은 `right-sidebar`라서 우측 여백만 말하는 것 같지만 실제로 좌우 여백 모두에 사용되는 설정값이라고 한다.

![210721035416.png](/assets/images/210721035416.png)

블로그 메인화면에서 사용하지도 않으면서 괜히 게시글 제목만 줄바꿈시키는 우측 여백도 제거했다.

`_sass\minimal-mistakes\_archive.scss` 파일에서 `padding-right` 를 주석처리한다.

![210721035924.png](/assets/images/210721035924.png)

> Reference
- https://padomay-dev.github.io/jekyll/jekyll-sidebar-edit/