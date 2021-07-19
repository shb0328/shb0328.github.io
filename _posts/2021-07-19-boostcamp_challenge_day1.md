---
layout: "single"
title: "2021.07.19 TIL (Today I Learned)"
categories: ['Programming','TIL','BoostCamp-Challenge']
tags: ['Git','fork','Node.js','LTS','JavsScript','sort']
permalink : /TIL/day1
---
# TIL (Today I Learned)
**BoostCamp Challenge DAY-1**

- Study Git : fork
- Study Node.js : 설치 및 실행
- Study JavaScript : Array.prototype.sort()

## Study Git

Git은 2018년도에 SW학부로 전과를 준비하면서 생활코딩에서 이고잉님의 강의를 통해 처음 학습했었다. (https://opentutorials.org/course/1492/8035)

`add`, `commit`, `pull`, `push`, `branch` 정도는 혼자서도 종종 사용해왔던 기능들이라 어렵지 않았지만, <br>
이번에 부스트캠프를 통해 많은 사람들과 함께 저장소를 사용하면서 조금 생소한 기능을 접하게 되었다.

### **fork**

![210719205403.png](/assets/images/210719205403.png)

`fork`는 다른 사람의 github repository 우측 상단에 위 그림과 같은 fork 버튼을 눌러서 내 github repository에 복제해 오는 기능이다.<br>
github.io 블로그를 만들 때 한 번 사용해봤던 기능이다.<br> 
fork해 온 repository는 아래와 같이 표현된다.

```
<my ID>/<repository name> 
forked from <origin user>/<repository name>
``` 

**예시)**<br>
![210719205628.png](/assets/images/210719205628.png)

github.io 블로그는 원본 repository를 복제만해서 커스텀하여 나 혼자 사용하고 있지만,<br>
사실 fork한 repository는 원본 repository와 연결되어있다는 점이 중요하다.<br>
그래서 내가 fork해 온 repository에 변경사항을 적용하면 원본 repository랑 비교할 수도 있고,<br>
원본 repository에 변경사항이 생겼을 때도 fetch&rebase를 통해 내 repository에 적용시킬 수도 있다.<br>
원본 repository에 내 변경사항을 적용시킬 수 도 있는데,(**PR, Pull Request**)<br>
반드시 fetch&rebase를 선행하여 원본 repository의 최신버전과 내 repository의 최신버전을 맞춘 뒤 PR을 진행해야한다.<br>
오픈소스 프로젝트에 참여하고 싶다면, 이렇게 fork와 PR을 통해 Contribution이 가능하다.

### **fork vs. clone**

`fork`는 repository를 '**복제**'한다는 점에서 `git clone`과 헷갈릴 수 있다.<br>
clone은 remote repository에 있는 데이터를 local (PC)에 복제해오는 것이고,<br>
fork는 repository to repository로 repository를 복제해오는 것이다.

![210719212259.png](/assets/images/210719212259.png)

<br>

## Study node.js

### **설치 및 실행**

![210719215446.png](/assets/images/210719215446.png)

[node.js 공식 홈페이지](https://nodejs.org/en/)에서 본인의 운영체제에 맞는 버전을 다운로드할 수 있다. <br>
나는 Windows 64bit 이다.

설치가 완료되면 잘 설치되었는지 확인해준다.<br>
* `cmd` -> `node -v` : 버전 확인
* `cmd` -> `node` : node.exe 실행
※ javascript 코드를 interpreter환경에서 실행해볼 수 있다.

![210719132931.png](/assets/images/210719132931.png)

그 다음, VS Code에서 WorkSpace를 만들고, `hello.js` 파일을 작성했다.<br>
<ctrl+\`> 버튼으로 VS Code 에서 터미널을 열고 `node` 명령어를 통해 `hello.js` 파일을 실행해본다.

오잉 ? <br>
<span style='color:grey'>Error: Cannot find module 'C:\00_boostcamp\hello.js'</span>

![210719133334.png](/assets/images/210719133334.png)

경로를 잘 확인했어야지... ㅎㅎ

![210719133643.png](/assets/images/210719133643.png)

### **왜 최신버전(16.5.0)이 아니라 LTS 버전(14.17.3)을 대다수 사용자에게 추천할까?**

![210719215522.png](/assets/images/210719215522.png)

**LTS** : Long Term Support - 일반적인 경우보다 장기간에 걸쳐 지원하도록 특별히 고안된 소프트웨어의 버전 또는 에디션이다. ([위키](https://ko.wikipedia.org/wiki/%EC%9E%A5%EA%B8%B0_%EC%A7%80%EC%9B%90_%EB%B2%84%EC%A0%84) 참고)

소프트웨어는 개발되면 끝이 아니다.<br>
소프트웨어 공학에는 소프트웨어 수명주기(Software Life Cycle)라는 것이 존재하며, 유지보수단계라는 것이 있다.<br>
출시한 소프트웨어를 계속해서 운영하며 bug fix 및 시스템 안정화를 지원하는 단계이다.<br>
오랫동안 유지보수되는 소프트웨어는 더 신뢰할 수 있고 안정적이다.<br>

최신 버전은 게임에서 beta test server 같은 것이다.<br>
새로운 기능을 먼저 만나볼 수 있지만 예상치 못한 bug가 많고 안정적이지 않을 수 있다.

전 직장에서 사용하던 Ubuntu LTS 버전의 EOS(End Of Service)가 도래하여 버전업그레이드를 진행했던 경험이 있다.<br>
SW들은 서로 연관이 깊고, 특히 OS 라던지 프로그래밍 언어나 플랫폼의 버전을 바꾸게 되면 거기에 의존하고 있던 수많은 다른 SW들의 영향도를 파악해야한다. (Dependency, 의존성) <br>
사용하는 SW가 짧은 주기로 지원이 끝나서 신뢰를 잃은 현재 버전을 새버전으로 바꿔야주어야하는 것은 고역일 것이다.

그러므로 대다수 사용자에게 LTS 버전을 추천하는 것이다.

<br>

## Study JavaScript

### **Array.prototype.sort()**

기본 정렬 순서는 문자열의 유니코드 코드 포인트를 따른다.<br>
즉, 정수형 데이터도 문자열의 유니코드를 기준으로 정렬된다.<br>
정수형 데이터를 정상적으로 정렬하려면 compare 함수를 따로 정의해주어야한다.

```js
var arr = [10, 1, 5, 9, 500];

function compareNumbers(a, b) {
	return a - b;
}

arr.sort();
console.log(arr);

arr.sort(compareNumbers);
console.log(arr);
```

위 예시의 출력 결과는 다음과 같다.

![210719185318.png](/assets/images/210719185318.png)
 
기본적으로 정수형 데이터가 유니코드 기준 사전순으로 정렬되는 것을 확인할 수 있다.<br>
compareNumbers 함수를 사용하여 정수형 데이터들을 오름차순으로 정렬시켰다.

하지만, `a - b` 의 결과에 `NaN` 이나 `Infinity`가 포함되면 안정적인 정렬을 보장할 수 없다.<br>

```js
var a = 3000 - "af";
var b = "af" - 3000;

console.log(a);
console.log(b);
```

위 코드에서 a, b를 출력한 결과는 `NaN`이다.
숫자로 나타낼 수 없는 문자열과 숫자 사이에 사칙연산 결과는 `NaN`(JavaScript로 나타낼 수 없는 숫자)이다.

compareNumbers 함수의 실행 결과가 음수인지, 양수인지 판단하여 정렬하는 것이므로,<br>
이 경우 아래 코드 실행 결과를 보면 정렬 순서가 보장되지 않는 것을 확인할 수 있다.

```js
var arr1 = [3000, 3, "af", 10, "abc"];
var arr2 = ["af", 3, 10, 3000, "abc"];

function compareNumbers(a, b) {
    return a - b;
}

arr1.sort(compareNumbers);
arr2.sort(compareNumbers);

console.log(arr1);
console.log(arr2);
```

실행결과<br>
![210719230116.png](/assets/images/210719230116.png)

<br>

# TIT (Today I Thought)

모르는게 정말 많다.<br>
아는게 거의 없는 수준이다.<br>
너무 조급해 하지 말자.

<br>

>Reference

[github OpenSource project contribution 가이드](https://medium.com/react-native-seoul/hackatalk-pr%EA%B3%BC%EC%A0%95%EC%9D%84-%ED%86%B5%ED%95%B4-%EC%82%B4%ED%8E%B4%EB%B3%B4%EB%8A%94-github-contribution-%EA%B0%80%EC%9D%B4%EB%93%9C-75bc4edb195e)

[MDN-Array.prototype.sort()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
[[JavaScript] 숫자와 문자열 자료형 변환](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=magnking&logNo=220975303797)

[Node.js 14.17.3 Documentation](https://nodejs.org/dist/latest-v14.x/docs/api/)