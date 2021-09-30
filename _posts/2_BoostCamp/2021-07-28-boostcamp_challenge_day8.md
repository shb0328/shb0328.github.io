---
layout: "single"
title: "2021.07.28 TIL (Today I Learned)"
categories: ['BoostCamp-Challenge']
tags: ['Functional Programming','JavaScript','CatogoryTheory','Closure','Pure Function','Curry']
permalink : /TIL/day8
---
# TIL (Today I Learned)
**BoostCamp Challenge DAY-8**

- Study Functional Programming
    - 함수
    - 카테고리 이론
    - 순수함수
    - 클로저
    - 커리

## Study Functional Programming

수학적인 함수

함수(function)
카테고리(category) - 카테고리 이론, 정수론, 집합론
입력 -> 출력
 X   f   Y    

프로그래밍적인 함수

프로시저와 함수
타입 (수학에서 카테고리 이론을 차용)

전형적인 프로그래밍 함수
console.log()
print()
random()
readLine()
...

1급 객체 first-class citizen
- 함수를 타입으로 지정할 수 있다.
- 인자값으로 넘길 수 있다.
- 리턴값으로 받을 수 있다.
>함수 자체를 객체처럼 쓸 수 있다.


카테고리 이론

f : X -> Y  (morphism)
g : Y -> Z  (morphism)
f ο g : X -> Z (morphism) : 결합 법칙 (Composition)

함수 중심 프로그래밍

자료 처리를 수학적 함수의 계산으로 표현
상태와 가변 데이터 대신 불변 데이터를 사용하는 프로그래밍 패러다임
- 순수 함수 (Pure Function)
- 불변 (Immutable) 타입
- 일급 함수와 고차 함수
- 자동 메모리 관리
- 타입 시스템 (타입 추론)

순수 함수 (Pure Function)
- 함수 내부에서 처리한 내용이 외부에 영향을 주지 않는다.
- no side-effect (부가적인 영향 X)
- immutable (변경 불가한 데이터) : 변경이 필요하면 새로운 데이터를 생성한다.
- referential transparency (참조 투명성) : 외부 데이터를 참조하지 않는다.
- Lazy Evaluation (느긋한 계산)

locality
함수 내부의 local scope 에서만 무언가 일어나고 값이 처리되고 리턴되어야 함.

익명함수 vs 클로저
함수도 클로저의 일부.
클로저가 함수보다 상위 개념.
익명함수와 클로저는 구분할 줄 알자.

클로저 (closure)
- 람다계산식(lamda calculus) 구현체
- 익명 함수(anonymous function)로 작성 가능
- 선언된 범위(scope)의 변수를 캡처해서 저장하고 (선언적으로) 닫힘
- swift, kotlin, js 에서 클로저는 캡처한 변수를 참조(reference) : closure 들도 side effect 가 발생할 수 있다..! 바람직하지 않음

함수지만 이름없는 상태로 클로저에 전달할 수 있어서 표현식이 더 풍부해질 수 있다.

클로저?
닫는다. close 에서 유래
closure 를 선언한 코드안에 변수를 캡처해서 가둠!

no 반복문
재귀호출 사용하도록 연습 (recursion)
 -> 변화하는 값을 사용할 수 없어서 계속 값을 넘기고 받아야함

eager evaluation : 함수 호출 전에 모든 인자 목록을 계산해 놓음.
lazy evaluation : 실제 함수 호출시 그 값이 필요할 때까지 계산하지 않음. (메모리 최적화)
    let arr = [2+1, 3*2, 8/4]
    print_length(arr) 
    위 배열에 arr[0] 와 같이 요소에 직접 접근하기 전까지 2+1 은 계산되지 않는다.
    print_length만 실행한다면 배열의 길이만 계산되어 출력될 것.

함수를 호출할 때 마다 계속 복사하기 때문에,
실제로 메모리가 2배, 4배 증가하는 것을 막기위해,
일단 메모리를 참조하고 있다가, 실제 접근하는 순간(필요해서 사용할 때)에 계산 및 복사

함수형 프로그래밍 타입

Category > Functor > Monad(endo-functor)  -> Type > Type-class (mapping 가능) > Monad, Data-Type

모나드 타입을 명시하진 않지만, 개념을 알아두고 적용할 줄 알아야 한다.

Functor

monadic 
generic
optinal

커링과 함수합성


![210728213443.png](/assets/images/210728213443.png)

### **소주제**

- 요약

***키워드, 더 알아볼 것***

<details>
<summary> 접기/펼치기 </summary>
<div markdown="1">

내용

</div>
</details>

내용

<br>

## Study 대주제1

### **소주제**

- 요약

***키워드, 더 알아볼 것***

내용 

<br>

## Study 대주제1

### **소주제**

- 요약

***키워드, 더 알아볼 것***

내용 

<br>

# TIH (Today I Heard)

서버 세팅은 개발자의 기본 중의 기본, 개발의 기초 중의 기초!

<br>

>Reference

- [a](https://opentutorials.org/course/173)
- [b](https://www.virtualbox.org/manual/ch01.html)
- [c](https://www.virtualbox.org/manual/ch05.html#vdidetails)