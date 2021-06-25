---
layout: single
title : "Markdown 연습"
---

# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5
###### 제목6

내용

내용

N<sup>위첨자</sup>

N<sub>아래첨자</sub>

<span style="color:red">글자색</span>

<span style="color:green">글자색</span>

<span style="color:blue">글자색</span>

<span style="color:grey">글자색</span>

**굵은 글씨**

*기울임꼴*

~~취소선~~

`배경`

['표 만들기' 이동](#표-만들기)

* 리스트1
* 리스트2
* 리스트3
  * 하위 리스트1
  * 하위 리스트2 

1. 리스트1
2. 리스트2
3. 리스트3

[링크](https://shb0328.github.io/)

> 인용

```
코드
```

```java
//java 코드
import java.util.Scanner;

public class Main_bj_2739_구구단 {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();

        for (int i = 1; i <= 9; i++)
            System.out.println(n + " * " + i + " = " + (n * i));
    }
}

```

- [ ] to-do1
- [X] to-do2
- [ ] to-do3
- [X] to-do4

**github gist**

*using html syntax*

`<script src="https://gist.github.com/shb0328/622c9e7f7020e104f1af94cdcad36cdb.js"></script>`

<script src="https://gist.github.com/shb0328/622c9e7f7020e104f1af94cdcad36cdb.js"></script>

*using jekyll-gist*

`{% gist shb0328/622c9e7f7020e104f1af94cdcad36cdb %}`

{% gist shb0328/622c9e7f7020e104f1af94cdcad36cdb %}


#### 표 만들기

```markdown
|1|2|3|
|:---|---:|:---:|
|왼쪽정렬|오른쪽정렬|중앙정렬|
||확장||
|**굵은 글씨**|<span style="color:red">빨간색</span>|`코드`|
```

|1|2|3|
|:---|---:|:---:|
|왼쪽정렬|오른쪽정렬|중앙정렬|
||확장||
|**굵은 글씨**|<span style="color:red">빨간색</span>|`코드`|

#### Emoji 

[Emoji Cheat Sheet](https://www.webfx.com/tools/emoji-cheat-sheet/)
:heart: :green_heart: :blue_heart: :purple_heart: :smile:

vs code 에서 emoji 미리보기를 위한 extension download.

![210625140119.png](/assets/images/210625140119.png)

#### 수식 표현하기

1) https://latex.codecogs.com/eqneditor/editor.php 
2) html : h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> x + &theta;<sub>1</sub>x <br>
`h<sub>&theta;</sub>(x) = &theta;<sub>o</sub> x + &theta;<sub>1</sub>x`

#### 그리스 문자 및 기호

| 명령 | 기호 | 설명 | - |  
| --- | :---: | --- | --- |  
| `&ap;` | &ap; | 비슷하다 | almost equal, asymptotic |  
| `&fnof;` | &fnof; | 함수 | function, florin |  
| `&radic;` | &radic; | 루트 | square root, radical sign |  
| `&infin;` | &infin; | 무한대 | infinity | |  
| `&alpha;, &Alpha;` | &alpha;, &Alpha; | 알파 | |  
| `&beta;, &Beta;` | &beta;, &Beta; | 베타 | |  
| `&delta;, &Delta;` | &delta;, &Delta; | 델타 | |  
| `&epsilon;, &Epsilon;` | &epsilon;, &Epsilon; | 입실론 | |  
| `&gamma;, &Gamma;` | &gamma;, &Gamma; | 감마 | |  
| `&sigma;, &Sigma;` | &sigma;, &Sigma; | 시그마 | |  
| `&omega;, &Omega;` | &omega;, &Omega; | 오메가 | |  
| `&lambda;, &Lambda;` | &lambda;, &Lambda; | 람다 | |  
| `&rho;, &Rho;` | &rho;, &Rho; | 로우 | |  
| `&sum;, &Sum;` | &sum;, &Sum; | 합계 | |  
| `&int;, &Int;` | &int;, &Int; | 인티그랄 | |  
| `&eta;, &Eta;` | &eta;, &Eta; | 에타 | |  
| `&zeta;, &Zeta;` | &zeta;, &Zeta; | 제타 | |  
| `&theta;, &Theta;` | &theta;, &Theta; | 세타 | |  
| `&phi;, &Phi;` | &phi;, &Phi; | | |  
| `&psi;, &Psi;` | &psi;, &Psi; | | |  

>출처 : https://github.com/zeuseyera/Markdown_TongDal-kr