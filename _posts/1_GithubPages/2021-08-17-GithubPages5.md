---
layout: single
title: "Github pages 블로그 Category 만들기"
categories: ['Github Pages']
tags: ['github pages','YFM','liquid']
permalink : /GithubPages/5
---

> 이 글은 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)를 기준으로 작성되었다.

<br>

# 배경지식 about Jekyll

## **YFM** (YAML Front Matter)
- YAML(야믈)은 XML, JSON과 같은 데이터포맷이다.
  - Jekyll (Static Website Builder) 에서 Github pages 블로그를 Build할 때 읽어들이는 데이터포맷이다.
  - https://www.inflearn.com/questions/16184
- YFM 블록이 포함된 모든 파일은 Jekyll에서 특수 파일로 처리된다.
  - 유효한 형식 : 파일의 첫 번째 내용으로, `---` (triple-dashed lines) 사이에 미리 정의된 변수들 (layout, title etc.) 또는 사용자정의 변수들의 값을 세팅한다.
  - YFM에서 설정된 변수들은 다양한 위치에서 Liguid tag를 사용해서 접근될 수 있다.

## **Liquid**
- Jekyll 에서 사용하는 탬플릿 언어 (templating language)
- Main Components
  - objects : 정의된 변수들을 페이지에 출력하기위해 사용한다.
    - 형식 : `{% raw %}{{ variables }}{% endraw %}`
  - tags : if문, 반복문 등을 사용해서 흐름을 제어하기위해 사용한다.
    - 형식 : `{% raw %}{% logic %}{% endraw %}`
  - filters : value를 정해진 filter에 맞게 변경하기위해 사용한다.
    - 형식 : `{% raw %}value | filter{% endraw %}`
    - 자세한 내용 : https://jekyllrb.com/docs/liquid/filters/

<br>

# Tag & Category 

>[취미로 코딩하는 개발자님의 블로그](https://devinlife.com/howto%20github%20pages/category-tag/)를 참고하여 작업했다.

글을 포스팅할 때 마다 YFM에 적어줬던 Tags와 Categories는 게시글 하단에 이렇게 보여지고 있다. 하지만, Tag나 Category별로 게시글을 볼 수는 없는 상황이다.

![210817150511.png](/assets/images/210817150511.png)

Tag나 Category를 눌러보면 404 File Not Found Error가 뜬다.

![210817150527.png](/assets/images/210817150527.png)

## 1. 페이지 만들기

새로운 글을 포스팅하려면 `_post` 폴더에 md 파일을 작성하듯이 새로운 페이지를 추가해주기위해 `_pages` 폴더를 만들고 md 파일을 작성해준다.

![210817150812.png](/assets/images/210817150812.png)

![210817150925.png](/assets/images/210817150925.png)

![210817151652.png](/assets/images/210817151652.png)

html 파일을 새로 만들어도 페이지가 새로 생기겠지만, html 파일은 주로 layout에 정의하고 실제사용되는 페이지는 md파일로 만들고 정의된 layout을 상속해서 사용하는 방식이 맞는 것 같다. 그리고 minimal-mistakes 테마는 이미 `categories layout`을 제공하고 있으니까 사용하겠다. (`tags`도 마찬가지)

![210817151031.png](/assets/images/210817151031.png)

![210817151631.png](/assets/images/210817151631.png)

이제 게시글 하단에 categories 또는 tag를 누르면 404에러가 뜨지않고 이런식의 페이지로 이동된다.

![210817152321.png](/assets/images/210817152321.png)

게시글 하단에 categories와 tags 관련 소스는 설정파일의 #Archives에서 찾을 수 있다.

![210817151202.png](/assets/images/210817151202.png)

## 2. 네비게이션 만들기

게시글 하단에 categories와 tags를 누르지 않고도 우측 상단에 `Categories`, `Tags` 버튼(?)을 만들어서 해당 페이지로 이동하게 하고 싶다.

![210817153354.png](/assets/images/210817153354.png)

기존에 minimal-mistakes 테마에서 붙여놓은 `About me`, `Posts`를 힌트로 소스를 좀 찾아보니 저 우측상단 부분에 정의된 버튼(?)들을 네비게이션이라고 부르는 것을 알아냈다. `_data/navigation.yml` 파일에서 찾을 수 있다.

![210817153617.png](/assets/images/210817153617.png)

기존에 `About me`, `Posts`도 누르면 404 에러가 뜨던 상황이었으므로 이참에 아래와 같이 수정해주었다.

`Posts` 를 누르면 블로그 메인페이지(/index.html)로 이동하도록 소스 내에 주석을 참고해서 url에 `/`을 적어주었고,

`About me` 를 누르면 (아직 미완성된) resume 페이지로 이동하도록 일단 `_pages/about-me.md` 파일을 만들고 permalink 를 `/about_md/`로 설정해서 네비게이션 url에 적어주었다.

그리고 원하던 `Categories`, `Tags` 도 아래와 같이 추가했고 잘 동작한다.

```yml
main:
   - title: "About Me"
     url: /about_me/
   - title: "Posts"
     url: /
   - title: "Categories"
     url: /categories/
   - title: "Tags"
     url: /tags/
```

![210817160056.png](/assets/images/210817160056.png)

<br>

*조만간 마구잡이로 적어놓은 게시글들의 category와 tag를 다 정리해야지..!*

>Reference
- https://devinlife.com/howto%20github%20pages/category-tag/
- https://jekyllrb.com/docs/front-matter/
- https://jekyllrb.com/docs/pages/
- https://jekyllrb.com/docs/step-by-step/08-blogging/#layout