---
layout: "single"
title: "Github Pages 블로그에 포스팅만해도 내 Github에 잔디가 심어졌으면 좋겠다."
categories: ['Github Pages']
tags: ['Github','commit','bare clone','mirror push','Why are my contributions not showing up on my profile?']
permalink : /GithubPages/6
---

<br>

| Before | After |
| :---: | :---: |
|<img src="/assets/images/210908003951.png" width="220px" height="200px">|<img src="/assets/images/210908010358.png" width="220px" height="200px">|

-----

블로그에 글을 작성하기 위해 Github에 commit과 push를 하고 있지만, 그에 따른 잔디가 심어지고 있지 않은 것을 발견했다. (정말 뒤늦게)

예전에 알고리즘 문제를 풀고 commit한 이력이 잔디가 심어지지 않아서, 알아보니 계정에 등록된 email과 사용중이던 git 설정에 global configure email이 달랐던 것이 원인이라 해결한 적이 있었다.

그러니까 이번엔 email 문제는 아닌 것이다.

구글링 끝에 Github Docs 에서 원인을 찾았다.

## 😥Why are my contributions not showing up on my profile?

## 😊Commits made in a fork will not count toward your contributions.

fork해 온 repository에는 commit을 해도, 카운트되지 않는다.

내 블로그는 `mmistakes/minimal-mistakes` repository를 fork해와서 사용중이었으므로 혼자 아무리 commit을 해도 잔디가 심어지지 않는 것이었다.

<br>

# Github Pages 블로그에 포스팅만해도 내 Github에 잔디가 심어졌으면 좋겠다.

Github Pages 블로그를 만들 때는 주로 누군가 공유해놓은 테마(repository)를 fork해서 시작하게된다.

블로그에 포스팅을 하려면 commit/push 를 하게 되는데, fork한 repository에 발생된 commit은 contribution으로 카운트되지 않아서 잔디가 심어지지 않는다.

잔디를 심고싶다면 처음부터 repository를 fork하지말고, 로컬에 내려받았다가 새로 만든 내 remote repository에 연결하여 push해 줄 수 있겠다.

하지만, 이미 fork해서 사용중이었고 얼마안되지만 그래도 그동안의 commit 이력을 살리고 싶었다.

감사하게도 아래의 친절한 블로그를 따라하여 해결했다. 🙇‍♀️

[감사한 블로그](https://soranhan.tistory.com/11)

-----

```bash
git clone --bare -b master --single-branch https://github.com/shb0328/shb0328.github.io.git
cd https://github.com/shb0328/shb0328.github.io.git
git push --mirror https://github.com/shb0328/new.git
cd ..
rm -rf https://github.com/shb0328/shb0328.github.io.git
```

![210908005039.png](/assets/images/210908005039.png)

github repository 에서 `new`라는 이름의 repo를 새로 만들고, 위와 같이 clone, push 한 뒤, 마지막으로 `shb0328.github.io` repo의 이름을 `a`로 바꾸고 `new` repo의 이름을 `shb0328.github.io`로 바꿔주었다.

-----

<br>

# 그렇다면, git clone 할때 `--bare` 옵션은 무엇이고, git push 할때 `--mirror` 옵션은 무엇일까?

>이것을 이해하기 위해 이고잉님의 ['지옥에서 온 GIT' - git의 원리](https://opentutorials.org/course/2708) 수업을 빠르게 수강했다. [정리한 내용은 여기에](https://shb0328.github.io/Git/1)

## 🥕git push --mirror

![211001020206.png](/assets/images/211001020206.png)

일반 push는 local refs/heads/branch에 기록된 commit으로 remote refs/remotes/remote/branch의 내용을 업데이트하는 반면에, mirror push를 하면 refs/ 폴더 아래의 '모든' 참조가(즉 branch들) remote repository에 그대로 미러링된다. 

테스트를 위해 github에 'test1', 'test2' remote repository를 각각 만들었다.

![211001063118.png](/assets/images/211001063118.png)

로컬에 'gittest' 폴더를 생성하고 local git repository를 만들어서 'main' branch에 3개, 'exp' branch에 4개의 commit을 만들었다.

![211001063343.png](/assets/images/211001063343.png)

gittest repository에 test1, test2 를 연결했다.

![211001063408.png](/assets/images/211001063408.png)

![211001063424.png](/assets/images/211001063424.png)

exp branch에 checkout된 상태로 test1 repo에는 `git push` 명령어를 실행했고,

main branch에 checkout된 상태로 test2 repo에는 `git push --mirror` 명령어를 실행했다.

![211001063537.png](/assets/images/211001063537.png)

github에서 remote repository들의 상태를 확인해보니 test1 repo는 exp branch 하나만 push되어 있는 반면에, test2 repo는 모든 branch와 모든 commit이 그대로 미러링되어있는 것을 확인할 수 있었다.

![211001063805.png](/assets/images/211001063805.png)

![211001063740.png](/assets/images/211001063740.png)

## 🥕git clone --bare

![211001020107.png](/assets/images/211001020107.png)

*bare git repository를 만든다. 이것은 디렉토리를 만들고 `.git` 폴더를 만드는 대신에 디렉토리 자체를 `$GIT_DIR` 로 만든다.*

git을 이용해서 버전관리하고 싶은 디렉토리에서 `git init` 명령어를 통해 `.git` 폴더가 생성되고 그때부터 해당 폴더는 git을 통해 버전관리가 이루어진다.

그런데 디렉토리 자체를 `$GIT_DIR`로 만든다는게 무슨 뜻인가...

![211001020819.png](/assets/images/211001020819.png)

`$GIT_DIR`는 `.git`폴더의 위치라고 정의한다. 그렇다면 디렉토리 안에 `.git`폴더를 만드는게 아니라 그 디렉토리자체를 `.git`으로써 사용한다는 것이다.

결국 `.git` 폴더란 실제 파일이나 폴더가 아니라 commit 등의 정보를 저장하고 있고,

bare git repository란 `.git` 폴더를 말한다고 볼 수 있고,

그래서 repository를 `--bare` 옵션으로 clone 하게 되면 실제 파일들을 clone 해오는 것이 아니라 commit 등의 정보만 clone 한다는 것이다.

### 🔎**bare clone vs. non-bare clone**

bare clone 과 non-bare clone의 차이를 눈으로 확인해보기 위해 테스트를 진행했다.

로컬에 'gittest2' 와 'gittest3' 폴더를 만들고, github에 'test3' remote repository를 만들었다.

gittest2 폴더에서는 test2 저장소로부터 non-bare clone을 수행했다.

![211001065354.png](/assets/images/211001065354.png)

a.txt 파일과 b.txt 파일이 다운로드되었고 `.git` 폴더가 생성되었으며, `.git/refs/heads/` 경로를 확인해보니 main branch만 clone 된 것을 확인할 수 있다.

![211001065330.png](/assets/images/211001065330.png)

gittest3 폴더에서는 test2 저장소로부터 bare clone을 수행했다.

![211001065633.png](/assets/images/211001065633.png)

a.txt 파일과 b.txt 파일 뿐만 아니라 `.git` 폴더도 보이지 않는다. `.git` 폴더 안에 있어야할 폴더와 파일들이 다운로드되었다.

그런데 `.git/refs/heads/` 경로를 확인해보니 아무것도 없다.

![211001070148.png](/assets/images/211001070148.png)

하지만 test3 repo에 mirror push를 실행했더니 test2 repo가 그대로 복사된 것을 확인할 수 있었다.

`config` 파일을 확인해보니 test2 repo가 origin이름으로 연결되어있고, `packed-refs` 파일에 branch 정보가 적혀있다.

![211001070317.png](/assets/images/211001070317.png)

gittest3은 원본 저장소 (test2 repo) 정보를 알고 있으니 직접 찾아가서 mirror push에 필요한 정보를 가져오는건지, 아니면 `packed-refs`가 `refs` 폴더를 압축한 것이고 `refs` 폴더와 다름없는 역할을 하기 때문에 미러링이 성공한 것인지 궁금했다.

'test4', 'test5' repo를 생성하고, 

**1**. `packed-refs` 파일 내용을 지우고 test4 repo에 mirror push

![211001070816.png](/assets/images/211001070816.png)

**2**. 1번 원복 후, test2 repo 삭제하고 test5 repo에 mirror push

![211001071025.png](/assets/images/211001071025.png)

![211001070917.png](/assets/images/211001070917.png)

원본 저장소의 존재유무와는 상관이 없고, `.git/refs/heads/` 경로에 branch 파일이 없어도 `packed-refs`에 branch가 정의되어 있으면 mirror push가 가능하다는 결과를 확인할 수 있었다.

(그럼 `packed-refs` 파일이 있는데 구지 비어있는 `refs` 폴더는 왜 만들어지는 것일까,,)

+다시보니 objects 폴더 내용도 다르다.

![211001071333.png](/assets/images/211001071333.png)

bare clone을 하면 가능한 압축해서 최소한의 용량만 clone 되는 것 같다는 생각이 든다. 

### 참고 : bare repository를 사용하는 이유

https://webisfree.com/2017-05-10/git-bare-repository%EB%9E%80

*공유하기위한 목적으로 bare repo를 생성합니다. 다수의 작업자, 프로젝트 참가자의 변경 사항을 공통으로 관리하기 위한 저장소로 사용할 수 있습니다.*

라고 하는데, 아직 와닿지는 않는다.

테스트 경험으로는 remote repository 복제가 목적일 때, 최소한의 용량만 빠르게 clone 할 수 있다는 점이 장점으로 느껴진다.

<br>

>Reference
- https://soranhan.tistory.com/11
- https://docs.github.com/en/repositories/creating-and-managing-repositories/duplicating-a-repository
- https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/managing-contribution-graphs-on-your-profile/why-are-my-contributions-not-showing-up-on-my-profile
- https://git-scm.com/docs