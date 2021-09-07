---
layout: "single"
title: "Github 블로그에 포스팅만해도 Github에 잔디가 심어졌으면 좋겠다."
categories: ['github pages']
tags: ['Github','commit','bare clone','mirror push','Why are my contributions not showing up on my profile?']
permalink : /GithubPages/8
---

작성중

## 😥Why are my contributions not showing up on my profile?

-----

| Before | After |
| :---: | :---: |
|<img src="/assets/images/210908003951.png" width="220px" height="200px">|<img src="/assets/images/210908010358.png" width="220px" height="200px">|

<br>

```bash
git clone --bare -b master --single-branch https://github.com/shb0328/shb0328.github.io.git
cd https://github.com/shb0328/shb0328.github.io.git
git push --mirror https://github.com/shb0328/new.git
cd ..
rm -rf https://github.com/shb0328/shb0328.github.io.git
```

![210908005039.png](/assets/images/210908005039.png)

github repository 에서 `shb0328.github.io` repo의 이름을 `a`로 바꾸고 `new` repo의 이름을 `shb0328.github.io`로 바꿔주었다.

-----

## 🥕git clone --bare

## 🥕git push --mirror

>Reference
- https://soranhan.tistory.com/11
- https://saengmotmi.netlify.app/trouble%20shooting/github%EC%97%90-%EC%9E%94%EB%94%94%EA%B0%80-%EC%8B%AC%EC%96%B4%EC%A7%80%EC%A7%80-%EC%95%8A%EC%9D%84-%EB%95%8C/
- https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-graphs-on-your-profile/why-are-my-contributions-not-showing-up-on-my-profile