---
layout: single
title: "Github pages 블로그 font 설정"
categories: ['github pages']
---

이 글은 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)를 기준으로 작성되었다.

# 블로그 font 바꾸기

[Google Web Fonts](https://fonts.google.com/)에 접속하여 마음에 드는 폰트를 고른다.<br>
filter 와 search 기능을 이용해 마음에 드는 font를 찾을 수 있다.

![210721022431.png](/assets/images/210721022431.png)

마음에 드는 폰트를 골랐으면 size도 조절해보고, Regular 400과 Bold 700 중 골라서 `Select this style` 버튼을 누른다. 

![210722002026.png](/assets/images/210722002026.png)

`Select this style` 버튼을 누르면 우측에 web에서 해당 폰트를 적용시키기 위한 코드를 `Use on the web` 탭에서 생성해준다.  `@import` 코드를 복사해서 `assets/css/main.scss` 파일에 추가한다. 폰트 이름을 `_sass/minimal-mistakes/_variables.scss` 파일에 추가한다.

![210721030003.png](/assets/images/210721030003.png)

![210721030053.png](/assets/images/210721030053.png)


💜 [눈누](https://noonnu.cc/) 에도 Google Web Font 처럼 여러가지 무료 폰트를 제공한다.

<br>

# 블로그 font size 변경

minimal-mistakes 테마에서 기본으로 제공해주는 폰트 사이즈가 너무 커서 항상 마음이 불편했다.

`_sass/minimal-mistakes/_reset.scss` 파일에서 사이즈를 변경해줄 수 있다.

Google Web Fonts 에서 테스트해본 중 가장 마음에 드는 사이즈로 변경해줬다.

![210721030336.png](/assets/images/210721030336.png)

> Reference
- https://hyeonjiwon.github.io/blog/글꼴-변경/
- https://danggai.github.io/github.io/Github.io-블로그-폰트-크기-조절하기/