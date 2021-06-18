---
layout: single
title: "Paste Image 이용하여 VS Code 에서 MD파일에 이미지 추가하기"
categories: ['github pages','paste image','vs code','markdown']
---

블로그 포스팅을 위해 md 파일을 작성할 때 Visual Studio Code 를 이용한다면, 이미지를 추가하기 위해 **Paste Image** Extension을 사용하면 편리하다.

VS Code Extensions 메뉴에서 paste image를 검색하여 install 해준다.

![210615141506.png](/assets/images/210615141506.png) 

Paste Image 를 설치했다면 작성 중인 md파일에 복사한 이미지를 바로 붙여넣기 위해 `Ctrl+Alt+v` 만 해주면 된다.

이때 복사한 이미지가 md파일에 첨부되어지는 과정은, 

복사한 이미지가 **지정된 경로**에 **지정된 형식의 이름**으로 저장이되고, `![이름](이미지가 저장된 경로)`의 패턴을 md파일에 삽입해주는 것이다.

<br>

![210618161255.png](/assets/images/210618161255.png)

***File > Preferences > Settings > Extentions > Paste Image Configurations***

위 경로를 따라가면 이미지파일이 저장될 **경로**, 저장할 이미지파일의 **이름 형식**, md 파일에 첨부될 **패턴** 의 설정값을 자신의 환경에 맞게 바꿔줄 수 있다. 

prefix 와 surfix 는 필요에 따라 적절히 설정해주면 되고,

중요한 부분은 *Path, Name, Pattern* 과 관련된 부분이다.

아래 사진은 나의 설정값이다.

![210618161343.png](/assets/images/210618161343.png)
![210618161404.png](/assets/images/210618161404.png)

경로가 제대로 설정되었다면 vs code 에서 md파일의 preview 를 확인했을 때 이미지가 정상적으로 보여져야한다. 

>Reference

[vscode-paste-image](https://marketplace.visualstudio.com/items?itemName=mushan.vscode-paste-image)