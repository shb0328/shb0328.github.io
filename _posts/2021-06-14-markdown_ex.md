---
layout: single
title: "Markdown 연습"
categories: ['markdown']
---

# 제목1
## 제목2
### 제목3
#### 제목4
##### 제목5
###### 제목6

내용

내용

<span style="color:red">글자색</span>

<span style="color:green">글자색</span>

<span style="color:blue">글자색</span>

<span style="color:grey">글자색</span>

**굵은 글씨**

*기울임꼴*

~~취소선~~

* 리스트1
* 리스트2
* 리스트3

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

**github gist**

`<script src="https://gist.github.com/shb0328/622c9e7f7020e104f1af94cdcad36cdb.js"></script>`

<script src="https://gist.github.com/shb0328/622c9e7f7020e104f1af94cdcad36cdb.js"></script>

`{% shb0328/622c9e7f7020e104f1af94cdcad36cdb %} using jekyll-gist`

{% shb0328/622c9e7f7020e104f1af94cdcad36cdb %}

- [ ] to-do1
- [X] to-do2
- [ ] to-do3
- [X] to-do4

