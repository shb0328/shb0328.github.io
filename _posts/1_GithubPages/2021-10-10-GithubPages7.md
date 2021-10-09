---
layout: "single"
title: "Github Pages minimal-mistakes skin 살짝 바꿔보기"
categories: ['Github Pages']
tags: ['github pages','Github', 'minimal-mistakes skin']
permalink : /GithubPages/7
---

# 아주 별거 아닌 블로그 스킨 색상 살짝 바꿔보는 포스팅

> 이 글은 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)를 기준으로 작성되었다.

minimal-mistakes 블로그는 기본으로 아래와 같은 skin을 제공한다.` _config.yml` 파일에서 확인할 수 있다.

```yml
minimal_mistakes_skin    :  "default" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"
```

![211010010057.png](/assets/images/211010010057.png)

[이미지 출처](https://github.com/mmistakes/minimal-mistakes)

이 중에서 `air` 스킨이 마음에 들어서 사용하고 있었는데, 최근 게시물에 자주 사용하는 💜 이모티콘의 보라색이 마음에 들어서 깔맞춤을 하고 싶다는 생각이 들었다.

그림판 스포이드, 네이버 색상 팔레트를 이용해서 💜 이모티콘의 보라색을 추출했다.

MS 기준이고 결과는 `#886DE4` 이다. *~~내 눈에 보이는게 중요하지...~~*

![211010010620.png](/assets/images/211010010620.png)

`air` 스킨의 `scss` 파일을 복사해서 `purpleAir` 파일을 만들고, `$primary-color`만 값을 바꿔주었다.

![211010011540.png](/assets/images/211010010748.png)

 `_config.yml` 파일에서 `minimal_mistakes_skin` 값을 `purpleAir` 로 변경하면 끝이다.

![211010011540.png](/assets/images/211010010832.png)

## 결과 비교

| Before | After |
| :---: | :---: |
|<img src="/assets/images/211010010307.png" width="480px" height="400px">|<img src="/assets/images/211010010346.png" width="480px" height="400px">|

