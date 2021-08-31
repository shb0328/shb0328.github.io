---
layout: single
title: "Github Pages 블로그 만들기 (feat.빌드오류)"
categories: ['github pages','active log','source tree','jekyll','Liquid','jekyll-gist']
permalink : /GithubPages/1
---

github pages 블로그를 생성하였다.

[youtube 영상](https://www.youtube.com/watch?v=ACzFIAOsfpM)을 참고하여 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)테마를 fork 하였다.

처음에는 github 사이트의 remote repository 내에서 몇 차례 jekyll config 파일을 수정했다.

프로필 이름 변경 등등 수정사항이 정상적으로 반영됨을 확인했다.

그 후에는 remote repository 소스를 로컬에 clone 한 뒤 로컬에서 config 파일 수정을 추가로 진행 하였고 source tree를 통해 commit&push 했다.

그런데, 아무리 새로고침을 해봐도 블로그에 변경사항이 적용되지 않는 문제가 발생했다.

1. 서버에 반영되기까지 최대 10분까지의 시간이 걸릴 수 있다.
2. source tree로 push한 소스가 remote repository에 정상적으로 반영이 되었는지 확인한다.
3. 새로고침할 때 웹브라우저 캐시를 삭제해준다. (ctrl+F5, ctrl+r)

처음엔 위 3가지 경우에서 고민했다.
하지만 결국 문제를 찾을 수 없어 repository를 삭제하고 다시 테마를 fork 해왔다.

마찬가지로 github 사이트 내에서 수정사항은 블로그를 새로고침할 때마다 정상적으로 반영이 되었는데,

remote repository 소스를 로컬에 clone 한 뒤 로컬에서 작업한 수정사항을 source tree를 통해 commit&push 한 내용부터는 반영이 되지 않기 시작했다.

source tree가 문제인가 고민하며 삽질을 시작했다...

그러던 중 remote repository 내에 Environments 탭을 발견하였고,
github-pages 의 Activity Log 를 확인할 수 있다는 사실을 알아냈다.

![210615140130.png](/assets/images/210615140130.png)

그런데, 가장 최근 Activity Log의 commit hash(commit 고유번호)가 좀 이상하다.

![210615140200.png](/assets/images/210615140200.png)

가장 최근 commit hash 가 아닌 것이다.

![210615140253.png](/assets/images/210615140253.png)

구글링 끝에, 
'Setting > Pages' 메뉴에서 아래와 같은 에러메세지가 발생하고 있던 것을 발견했다.

```
Your site is having problems building: 
The tag shb0328 on line 64 in _posts/2021-06-14-markdown_ex.md is not a recognized Liquid tag.
For more information, 
see https://docs.github.com/github/working-with-github-pages/troubleshooting-jekyll-build-errors-for-github-pages-sites#unknown-tag-error.
```

![210615140437.png](/assets/images/210615140437.png)

알려준 [링크](https://docs.github.com/github/working-with-github-pages/troubleshooting-jekyll-build-errors-for-github-pages-sites#unknown-tag-error)를 따라가보니 Unknown tag error 에 대한 설명이 적혀있었다.

![210615140549.png](/assets/images/210615140549.png)

markdown 문법 연습을 위해 작성한 아래 파일에서 jekyll에서 사용하는 Liquid 템플릿 언어의 문법 오류 때문에 빌드가 안되고 있었던 것이다.

<span style="color:grey">(github gist를 jekyll-gist를 이용해서 불러오는 코드 {% gist ... %} 에서 gist를 빼먹었다.)</span>

![210615140623.png](/assets/images/210615140623.png)

우연히도 로컬에서 작성한 파일을 업로드 할때만 오류가 발생해서 원인을 잘못 추측하고 초반에 삽질을 많이 했다. 

결론적으로 github 사이트에서 업로드하든, 로컬에서 수정 후 push하여 업로드하든 상관없었다.

<span style="color:red">*역시 뭐든 디버깅하는 법부터 배워야지 ^^!*</span>

+나중에 발견한 사실인데, 빌드가 실패하면 GitHub에 가입한 메일로 메일이 오고 있었다...

![210615141016.png](/assets/images/210615141016.png)

![210615141011.png](/assets/images/210615141011.png)

+참고

빌드 중일 때 'Setting > Pages' 화면

![210615144410.png](/assets/images/210615144410.png)

빌드가 성공했을 때 'Setting > Pages' 화면

![210615144425.png](/assets/images/210615144425.png)

>Reference

[YouTube - 깃헙(GitHub) 블로그 10분안에 완성하기](https://www.youtube.com/watch?v=ACzFIAOsfpM)

[Jekyll-themes](https://github.com/topics/jekyll-theme)

[Jekyll Docs about Posts](https://jekyllrb.com/docs/posts/)

[GitHub Docs about Environments](https://docs.github.com/en/actions/reference/environments)

[GitHub Docs about Activity Log](https://docs.github.com/en/github/administering-a-repository/managing-repository-settings/viewing-deployment-activity-for-your-repository)

[GitHub Docs about Unknown tag error](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/troubleshooting-jekyll-build-errors-for-github-pages-sites#unknown-tag-error)

[Jekyll Docs about Variables](https://jekyllrb.com/docs/variables/)

[Jekyll Docs about Liquid](https://jekyllrb.com/docs/liquid/)