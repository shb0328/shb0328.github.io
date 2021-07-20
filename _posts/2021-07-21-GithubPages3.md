---
layout: single
title: "Github pages 블로그 font 설정"
categories: ['github pages']
---

이 글은 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)를 기준으로 작성되었다.

# 블로그 font 바꾸기

[Google Web Fonts](https://fonts.google.com/)에 접속하여 마음에 드는 font를 고른다.<br>
filter 와 search 기능을 이용해 마음에 드는 font를 찾을 수 있다.

![210721022431.png](/assets/images/210721022431.png)

우측 `@import` 코드를 복사해서 `assets/css/main.scss` 파일에 추가한다. 

![210721030003.png](/assets/images/210721030003.png)

`_sass/minimal-mistakes/_variables.scss` 파일에 font 이름을 해당 위치에 추가한다.

![210721030053.png](/assets/images/210721030053.png)


Google Web Fonts 사이트에서 font size 를 조절해가면서 font 미리보기를 한 뒤 마음에 드는 사이즈로 블로그 font 사이즈도 변경하려고 한다.<br>

# 블로그 font size 변경

`_sass/minimal-mistakes/_reset.scss` 파일에서 변경해준다.

![210721030336.png](/assets/images/210721030336.png)

> Reference
- https://hyeonjiwon.github.io/blog/글꼴-변경/
- https://danggai.github.io/github.io/Github.io-블로그-폰트-크기-조절하기/