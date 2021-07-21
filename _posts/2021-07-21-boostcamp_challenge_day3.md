---
layout: "single"
title: "2021.07.21 TIL (Today I Learned)"
categories: ['Programming','TIL','BoostCamp-Challenge']
tags: ['Crawling','','','','','']
permalink : /TIL/day3
---
# TIL (Today I Learned)
**BoostCamp Challenge DAY-3**

- Study Crawling : DOM과 Selector, JSON
- Study LRU 알고리즘 : JavaScript로 구현하기
- Study JavaScript : 기본 입출력

## Study Crawling

### 🤔 왜 필요할까?

웹 서버와 웹 클라이언트가 요청을 보내고, 응답을 주고 받는 과정을 이해하고, 웹 브라우저가 동작하는 방식을 이해하는 것은 매우 중요하다. 그 중에서도 웹 크롤링으로 데이터를 자동화해서 수집하는 것은 필요한 기술이면서도, 법적으로 침해하지 않아야 하는 선을 지켜야 하는 기술이다. 웹 크롤링으로 수집한 데이터를 LRU 캐시 방식으로 처리하도록 구현해보면서 node 모듈을 다루고, 데이터를 처리하는 방식에 익숙해져야 한다.

### **먼저 이해할 것**

WEB 페이지는 일종의 문서(document)이다. 웹 브라우저를 통해 그 내용이 해석되어 웹 브라우저 화면에 나타나거나 HTML 소스 자체로 나타나기도 한다.

우리가 `.txt` 형식의 파일(문서)를 메모장과 같은 편집기로 실행시키는 것처럼, chrome과 같은 웹 브라우저를 이용해서 `.html`과 같은 형식의 파일(문서)를 실행시키는 것이다.

Windows의 경우 브라우저에서 `Ctrl + o`를 누르면 파일(문서)을 열 수 있는데, 이 것은 메모장(및 대부분의 프로그램)에서 파일을 여는 단축키와도 같다는 것을 깨달았다.

![210721215830.png](/assets/images/210721215830.png)
![210721220035.png](/assets/images/210721220035.png)

#### **DOM**

- 문서 객체 모델 (DOM, The Document Object Model)
    - 객체지향적 표현
    - nodes, property, method를 갖고 있는 object로 문서를 표현
- HTML, XML 문서의 프로그래밍 Interface
    - 문서의 구조화된 표현(structured representation)을 제공 
    - 프로그래밍 언어가 DOM구조에 접근 및 변경할 수 있는 방법을 제공
        - JavaScript와 같은 스크립팅 언어를 이용해 수정가능

#### **Selector**

- 

#### **JSON**

- 

### **Crawling**

- 

<br>

##  Study LRU 

### **JavaScript로 구현하기**

```
```

<br>

## Study JavaScript

### **readline**

- readline 모듈은 한 번에 한 줄씩 Readable 스트림 (예 : process.stdin)에서 데이터를 읽기위한 인터페이스를 제공합니다. 

***Readable 스트림***

process.stdin

<br>

# TIF (Today I Felt)

![210721223930.png](/assets/images/210721223930.png)

*모른다고 알게된 것*의 범위가 확장되고 있다.

<br>

>Reference

- [MDN - DOM](https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction)
- [node.js v14 doc - readline](https://nodejs.org/dist/latest-v14.x/docs/api/readline.html)
- [[Node.js]표준 입력 받기(readline)](https://velog.io/@yujo/node.js%ED%91%9C%EC%A4%80-%EC%9E%85%EB%A0%A5-%EB%B0%9B%EA%B8%B0)
- [LRU Cache Algorithm 정리](https://jins-dev.tistory.com/entry/LRU-Cache-Algorithm-%EC%A0%95%EB%A6%AC)