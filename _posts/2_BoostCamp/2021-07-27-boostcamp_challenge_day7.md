---
layout: "single"
title: "2021.07.27 TIL (Today I Learned)"
categories: ['BoostCamp-Challenge']
tags: ['OOP','Abstraction','Inheritance','Polymorphism','JavaScript','enum']
permalink : /TIL/day7
---
# TIL (Today I Learned)
**BoostCamp Challenge DAY-7**

- Study OOP : Abstraction, Inheritance, Polymorphism 
- Study SOLID Principles : SRP, LSP
- Study Javascript : enum

## Study OOP (Object-Oriented Programming)

- 클래스 객체 class 와 객체 인스턴스 instance, object
- 프로퍼티 property 와 메소드 method
- 캡슐화 encapsulation
- 상속 inheritance
- 다형성 polymorphoism
- 객체 관계와 설계 패턴 design pattern

🧐 달달 외우고 있는 객체지향 4대 특징 (Encapsulation, Abstraction, Inheritance, and Polymorphism) 말고 진짜 OOP를 이해해야한다.

### **추상화(abstraction)**

#### **프로시저 추상화 (procedure abstraction)** : 무엇을 해야하는지, **절차**에 대한 추상화 

- 간접 참조 (indirection) : 값 자체보다 컨테이너, 연결, 별명 등을 사용해서 우회해서 참조하는 방식
    - 기능분해 (functional decomposition)
    - 알고리즘 분해 (algorithm decomposition)

```js
function makeGradeCard(name, scoreList) { //high level
    let result = [];
    result.name = name;
    result.grade = getGrade(scoreList);
    return result;
}

function getGrade(scoreList) { //low level
    if(sum(scoreList) - getMax(scoreList) > 500) return "A";
    return "B";
}

function sum(arr) { //more low level
    let sum = 0;
    for(let v of arr) sum += v;
    return sum;
}

function getMax(arr) { //more low level
    let max = -1;
    for(let v of arr) max = max < v ? v : max;
    return max;
}
```

추상화 레벨을 설명해보려고 작성한 예시이다.

성적표를 만드는 함수 makeGradeCard를 호출하는 사용자는 name(이름)과 scoreList(점수목록)만 input으로 입력하면 된다. *어떻게 성적을 알아내는지에 대해서는 알 필요가 없다.*

`sum(), getMax() - getGrade() - makeGradCard()` 순서로 추상화레벨이 높아지는 것을 표현했다. sum() 함수는 getGrade() 함수보다 구체적이라고 할 수 있다. 반대로, getGrade() 함수는 sum() 함수보다 추상적이다.

>프로시저 (procedure) vs 함수 (function)<br>
>   : 과거에는 프로시저를 return 값 없이 절차만 기술하는 도구로써 함수와 용어적으로 구별하기도 했지만, 현대에는 큰 구별없이 사용되고 있다.

#### **데이터 추상화 (data abstraction)** : 무엇을 알아야하는지, **데이터**에 대한 추상화

- 추상화(abstraction) : 복잡한 자료, 모듈, 시스템 등으로부터 핵심적인 개념 또는 기능을 간추려 내는 것을 말한다. ([Wiki](https://ko.wikipedia.org/wiki/%EC%B6%94%EC%83%81%ED%99%94_(%EC%BB%B4%ED%93%A8%ED%84%B0_%EA%B3%BC%ED%95%99)))
    - 타입 추상화 : **abstract data type** (by 바바라리스코프)
        - 타입 정의 선언 
        - 타입 인스턴스를 다루는 오퍼레이션 집합을 정의
        - 제공하는 오퍼레이션으로 조작하도록 보호
        - 타입에 대한 여러 인스턴스를 생성
    - 데이터 중심 프로시저 추상화 : **object-oriented** (by 앨런케이)
        - 상속과 다형성 지원

🔎***class vs. instance vs. object***

![210728011835.png](/assets/images/210728011835.png)

A라는 class를 정의하면, A 타입의 instance를 여러개 만들 수 있다.
각 instance들은 고유한 property들을 가질 수 있고, class 에서 정의된 method들을 공유한다.
method가 정의된 class와 각각의 property를 갖고 있는 instance를 합쳐서 object (객체) 라고 부른다.

```java
class A { //class
    int property1;
    String property2;

    void method1() {}
    void method2() {}
    void method3() {}

    public A(int p1, String p2) {
        super();
        this.property1 = p1;
        this.ptoperty2 = p2;
    }
}

A a1 = new A(10, "a"); //instance
A a2 = new A(20, "aaa"); //instance
```

***예시***

![210727232012.png](/assets/images/210727232012.png)

### **Inheritance & Polymorpism**

상속은 class A가 가진 method와 property들을 class A를 상속한 class B에 물려주는 것이다.
class B는 class A가 물려준 것들 뿐만 아니라 class B에서 새로 정의한 method와 property도 사용할 수 있다.

다형성은 class A를 상속한 class B와 C에서 class A에서 상속해준 method를 각각 재정의(override) 하여 사용함으로써 method 이름은 같지만 상속받은 객체 B,C 각각의 특성에 맞는 method를 사용할 수 있게 해준다.

상속과 다형성을 잘 활용하면 객체의 재사용성을 높이고 추상도 높은 설계를 할 수 있다.

***예시1***

![210727232052.png](/assets/images/210727232052.png)

![210727233138.png](/assets/images/210727233138.png)

***예시2***

`Parents class`를 상속한 `Child class`에서 `f1(), f2(), f3()` 의 동작모습을 관찰한다.

```js
class Parents {
    constructor() {
        this.data1 = 1;
        this.data2 = 2;
    }

    f1 = () => console.log("I'm Parents - f()", this.data1, this.data2);
    f2 = () => console.log("I'm Parents - g()");
    f3() { //abstract method
        throw new Error("must override f3 method");
    }
}

class Child extends Parents {
    constructor() {
        super();
        this.data1 = 100;
    }
    f1 = () => console.log("I'm Child - f1()", this.data1, this.data2);
    f3 = () => console.log("I'm Child - f3()");
}

let arr = [];
let inf = new Parents();
let imp = new Child();
arr.push(inf);
arr.push(imp);

for (let obj of arr) {
    console.log(obj instanceof Parents);//true
    obj.f1();
    obj.f2();
    if (obj instanceof Child) obj.f3();
}
```

<br>

## Study Javascript : enum

javascript는 enum type을 지원하지 않는다.<br>
아래와 같은 방법으로 사용할 수 있다.

```js
const Enum = Object.freeze({ A: 0, B: 1, C: 2, D: 3, E: 4, F: 5, G: 6, H: 7 });

f = function (str) {
    let arr = [[10, 11], [12, 13]];
    console.log(Enum[str]); //0
    console.log(arr[Enum[str]]); //[10, 11]
}

console.log(Enum.C);//2
f("A");
```

typescript에서는 enum type을 지원한다. 다음에 사용해보자.

```ts
enum Enum {
  A, // 0
  B, // 1
  C  // 2
}
```

[더 알아볼 것 - TypeScript enum을 사용하지 않는 게 좋은 이유를 Tree-shaking 관점에서 소개합니다.](https://engineering.linecorp.com/ko/blog/typescript-enum-tree-shaking/)

## 😥 NOT DONE

- **SOLID** Principles
    - **S** - Single-responsiblity Principle (**SRP**)
    - **O** - Open-closed Principle
    - **L** - Liskov Substitution Principle (**LSP**)
    - **I** - Interface Segregation Principle
    - **D** - Dependency Inversion Principle

- SRP (Single-Responsibility Principle, 단일책임원칙)

- LSP (The Liskov Substitution Principle, 리스코프교환원칙)

```
3.3. Type Hierarchy
- 타입 계층은 서브 타입과 수퍼 타입으로 이루어진다.
- 하위 타입은 수퍼 타입의 모든 동작과 추가 기능을 이어받는다.
What is wanted here is something like the following substitution property [6]: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2, then S is a subtype of T.

여기에 필요한 것은 다음과 같은 치환(substitution) 원칙이다. S 타입의 객체 o1 각각에 대응하는 T 타입 객체 o2가 있고, T 타입을 이용해서 정의한 모든 프로그램 P에서 o2의 자리에 o1을 치환하더라도 P의 행위가 변하지 않는다면, S는 T의 하위 타입이다.
```
>Reference : https://johngrib.github.io/wiki/summary-Data-Abstraction-and-Hierarchy/

<br>

# TIW (Today I Watched)

점점 밀린 공부거리가 쌓여가고 있다..🤪<br>
공부를 DFS 방식으로 하는게 속이 편한데, 그러기엔 시간이 너무 부족하다.<br>

https://www.youtube.com/watch?v=3smc7jbUPiE&ab_channel=Project%EC%8A%A4%EB%85%B8%EC%9A%B0%EB%B3%BC

부캠에서 추천해준 영상인데, 질문을 잘하는 법과 질문에 잘 대답하는 법에 대해 생각해볼 수 있는 영상이다.<br>
Why 라는 질문을 할 때에는 내가 얼만큼 알고 있고, 어디까지 알고싶은지 잘 정의해야 한다.<br>
Why 라는 질문에 대답할 때에는 상대방이 얼만큼 알고있고, 어디까지 대답해줄지에 대해 고민해봐야한다는 내용이다.<br>

나는 스스로에게 질문하고 그 답을 찾는 과정(=공부)에 대해서도, 이 영상에서 말하듯이 파고들수록 "흥미롭지만" 일단은 (당장은 다음 질문에 대한 답을 찾기 위해) 세상의 요소로 받아들여야 할 것들은 인정하고 넘어가는게 시간 관계상 필요한 것 같다...

하지만 적어뒀다가 다음에 꼭 다시 확인해봐야겠다.

<br>

>Reference
- https://velog.io/@feelslikemmmm/JavaScriptClass
- https://mylife365.tistory.com/281
- https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design
- https://www.semanticscholar.org/paper/Data-Abstraction-and-Hierarchy-Liskov/36bebabeb72287ad9490e1ebab84e7225ad6a9e5?p2df
- https://blog.ndepend.com/solid-design-the-liskov-substitution-principle/