---
layout: "single"
title: "2021.07.20 TIL (Today I Learned)"
categories: ['Programming','TIL','BoostCamp-Challenge']
tags: ['Linux','Ubuntu','Virtual Box','Shell','ShellScript','crontab']
permalink : /TIL/day2
---
# TIL (Today I Learned)
**BoostCamp Challenge DAY-2**

- Study VM(Virtual Machine) : Virtual Box로 알아보는 VM, VM환경에 Ubuntu 설치, SSH
- Study ShellScript : #!/bin/sh
- Study crontab : cron, crontab

## Study VM(Virtual Machine)

### **가상 머신(VM, Virtual Machine)**

- 하드웨어를 소프트웨어적으로 구현해서 그 위에서 운영체제가 작동하도록하는 기술

![210720205100.png](/assets/images/210720205100.png)

***사용하는 이유?***

1. 여러 운영체제를 동시에 사용 가능 (윈도우에서 리눅스 등) 
2. 독립된 작업공간이 필요한 경우 (컨테이너의 역할 - a virtual machine and its virtual hard disks can be considered a container that can be arbitrarily frozen, woken up, copied, backed up, and transported between hosts.) 
    - 보안 : 의심되는 프로그램을 Gest 컴퓨터에 먼저 설치하여 바이러스나 오류로부터 Host 컴퓨터를 지킬 수 있다.
    - 백업 : 스냅샷을 이용하여 가상머신을 오류가 발생하기 전(프로그램 설치 전) 상태로도 쉽게 되돌릴 수 있다.
    - 테스트, DR (Disaster Recovery, 재해복구) 등
3. 통합 인프라
    - 하나의 머신(컴퓨터, 서버)에서 여러명에게 운영체제 환경을 제공 <span style='color:grey'>(instead of running many such physical computers that are only partially used, one can pack many virtual machines onto a few powerful hosts and balance the loads between them.)</span>

***스냅샷?***
- 가상머신의 중요한 특징
- 컴퓨터의 상태 (프로그램들,데이터 등)를 보관해두는 기능
- 일종의 백업

컴퓨터 단위의 버전관리같다는 느낌을 받았다.<br>
하나의 스냅샷이 Git에서 하나의 Commit같은 의미로 다가왔다.(하지만 스냅샷은 용량이 부족하면 적절히 삭제해주어야한다.)<br>
심지어 Clone(복제) 기능도 있다.

![210720160623.png](/assets/images/210720160623.png)

### **Virtual Box**

- 오라클에서 만든 가상머신 솔루션
- 오픈소스
- 무료!

[VirtualBox는 서버, 데스크탑 및 임베디드 사용을 대상으로 하는 x86 하드웨어용 범용 완전 가상화 장치입니다. - VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use.](https://www.virtualbox.org/wiki/VirtualBox)

### **Virtual Box 설치 및 실행**

[https://www.virtualbox.org/](https://www.virtualbox.org/)

![210720131500.png](/assets/images/210720131500.png)

홈페이지에서 원하는 버전의 Virtual Box 프로그램을 설치한다.

<details>
<summary>VirtualBox에서 가상머신 삭제</summary>
<div markdown="1">

설치하고 Virtual Box를 실행했는데 4학년 때 OS수업에서 사용했던 Ubuntu 가상 머신이 남아있어서 삭제해줬다.

![210720131729.png](/assets/images/210720131729.png)

![210720131929.png](/assets/images/210720131929.png)

![210720132129.png](/assets/images/210720132129.png)

그냥 삭제하면 되나 했는데, 전원 꺼짐 상태가 되었을 뿐이었다.(ㅋㅋ)

설정에 들어가서 경로를 확인해주고, 경로에 가서 폴더를 삭제해버렸다.<br>

![210720132007.png](/assets/images/210720132007.png)

![210720132257.png](/assets/images/210720132257.png)

하지만 여전히 Virtual Box에 남아있다...

실행시켜보았는데, 방금 삭제했던 폴더(OS class)말고 사용하던 가상머신을(.vmdk) 이미 예전에 삭제해놔서 실행은 안된다.<br>
그리고 삭제해줬던 폴더(.../VirtualBox VMs/OS class)는 가상머신외에 및 스냅샷, 로그 등의 데이터 저장용으로 Virtual Box가 만들어준 것이었는지,<br>
실행 동작을 했더니 해당 경로에 폴더가 다시 생성되었다.

![210720132505.png](/assets/images/210720132505.png)

![210720132952.png](/assets/images/210720132952.png)

저 가상머신을 목록에서 지워버리고 싶다.<br>
우클릭을 해보니 다른 아이콘의 삭제버튼이 보인다.

![210720133100.png](/assets/images/210720133100.png)

아까와는 다른메세지가 발생한다.

![210720133144.png](/assets/images/210720133144.png)

드디어 목록이 깨끗해졌다.

</div>
</details>

![210720133211.png](/assets/images/210720133211.png)

### **Ubuntu 20.04.2.0 LTS 다운로드**

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)<br>
위 사이트는 좀 느리기때문에... [여기서](http://mirror.kakao.com/ubuntu-releases/) 다운로드하면 좀 더 빠르다.

![210720131404.png](/assets/images/210720131404.png)

홈페이지에서 최신 LTS버전의 Ubuntu 이미지(iso)를 다운로드 받는다.

`iso` 파일을 다운로드폴더에 두고 싶지 않아서, C드라이브에 `VMs` 폴더를 만들고, 하위에 `images` 폴더를 만들고 그 안에 `iso` 파일을 옮겼다.

![210720141823.png](/assets/images/210720141823.png)

### **VirtualBox에 가상머신 생성**

Virtual Box에서 `새로만들기` 버튼을 클릭하고 내가 가상머신이름을 정한다.<br> 
가상머신과 관련된 파일이이 저장될 경로도 지정해준다.<br> 
`images/*.iso` 파일을 넣어 둔 `C:\VMs` 폴더로 지정해줬다.

![210720142450.png](/assets/images/210720142450.png)

`종류` 옆에 listBox를 눌러보면 여러가지 OS 종류가 나온다.<br>
Linux 기반의 Ubuntu를 사용할 것이므로 Linux를 선택하고, `버전`도 설치한 이미지파일과 같이 Ubuntu (64-bit)를 선택해준다.

![210720142057.png](/assets/images/210720142057.png)

'전문가모드'가 뭐지 하고 눌렀다가 설정값이 모두 초기화돼서 다시 작성했다.<br>
4학년 실습 때는 학교에서 가상하드를 제공해줬지만 이번에는 새로 만들어서 사용해야한다. <br>
Host PC 메모리가 8GB 이므로 default로 설정되어있던 1GB 정도만 사용하면 될 것 같다.<br>
그럼 결국 다 default를 사용하는거니까 가이드모드로 가상머신을 생성해도 되는 것이었다.

![210720143341.png](/assets/images/210720143341.png)

용량 10GB 의 가상하드디스크를 지정해준 `C:\VMs` 경로 아래 생성할 것이다.<br>
VirtualBox만 사용할 예정이므로 VDI로 생성하겠다.(무료!)

![210720143549.png](/assets/images/210720143549.png)

C드라이브 용량이 57.8GB 남았는데 10GB를 써도되는지 모르겠다.<br>

![210720143432.png](/assets/images/210720143432.png)

***하드 디스크 파일 종류***

- VDI (VirtualBox Disk Image) : VirtualBox 자체 컨테이너 형식 <span style='color:grey'>(Normally, Oracle VM VirtualBox uses its own container format for guest hard disks. This is called a Virtual Disk Image (VDI) file. This format is used when you create a new virtual machine with a new disk.)</span>
- VHD (Virtual Hard Disk) : Microsoft에서 사용하는 가상 하드 디스크 형식 <span style='color:grey'>(Oracle VM VirtualBox also fully supports the VHD format used by Microsoft.)</span>
- VMDK (Virtual Machine Disk) : VMware와 같은 다른 많은 가상화 제품에서 사용되는 널리 사용되는 개방형 VMDK 컨테이너 형식 <span style='color:grey'>(Oracle VM VirtualBox also fully supports the popular and open VMDK container format that is used by many other virtualization products, such as VMware.)</span>


드디어 가상머신을 생성했다.<br>
`C:\VMs\ubuntu 20.04` 경로에 가서 .vdi 파일이 생성된 것도 확인할 수 있다.

![210720150601.png](/assets/images/210720150601.png)

![210720150442.png](/assets/images/210720150442.png)

이제 설치해둔 ubuntu 이미지파일을 등록한다.<br>
`설정` -> `저장소` -> `컨트롤러:IDE` 우클릭 -> `광학 드라이브` -> `추가`

![210720151143.png](/assets/images/210720151143.png)

`시작`하고 등록해둔 시동디스크를 선택한다.

![210720151604.png](/assets/images/210720151604.png)

VM 실행창 우측 아래에 여러가지 VirtualBox 상태아이콘들이 있는데, 특히 가장 오른쪽에 키보드와 마우스와 대한 상태아이콘에 대해 팝업으로 설명해준다.<br>
아이콘에 마우스를 올려놔도 설명이 나온다.<br>

![210720154905.png](/assets/images/210720154905.png)

![210720152100.png](/assets/images/210720152100.png)

![210720152119.png](/assets/images/210720152119.png)

### **Ubuntu OS 설치**

이제부터는 VM에 우분투 os를 설치하는 과정이다.

`언어 - 한국어`

![210720152159.png](/assets/images/210720152159.png)

`최소 설치`

![210720152328.png](/assets/images/210720152328.png)

`디스크를 지우고 우분투 설치`<br>
파티션을 나누면 VM에서 듀얼부팅같은 것도 되는 건가...

![210720152506.png](/assets/images/210720152506.png)

`Seoul`

![210720152824.png](/assets/images/210720152824.png)

`ID/PW 생성`

![210720152953.png](/assets/images/210720152953.png)

꽤 긴 기다림끝에 설치가 끝났다.

본인계정으로 로그인하고 명령어 몇 개 날려봤다.

![210720162801.png](/assets/images/210720162801.png)

### **SSH를 이용한 VM 접속**

1. VM에서 SSH 서버를 연다.
2. SSH 프로토콜로 VM에 원격 접속한다.
    - 터미널에서 ssh 명령어를 이용한다.
    - PuTTY와 같은 SSH 클라이언트를 이용한다.
    - VS Code에서 'Remote-SSH' Extention을 이용한다.

#### 1. VM에서 SSH 서버를 연다.

root 계정 PW를 설정 한 뒤 root 계정으로 접속한다.

![210720162943.png](/assets/images/210720162943.png)

`dpkg -l | grep ssh` 명령어를 이용해 SSH서버가 설치되어 있는지 확인한다.<br>
library와 client만 설치되어있다.

![210720163109.png](/assets/images/210720163109.png)

`apt-get update` 명령어를 이용해 패키지 목록을 최신화한다.

![210720163203.png](/assets/images/210720163203.png)

`apt-get install openssh-server` 명령어를 이용해 아래 그림과 같은 추가 패키지들이 설치된다.

![210720163324.png](/assets/images/210720163324.png)

다시 `dpkg -l | grep ssh` 명령어를 이용해 확인해보면,<br>
library와 client외에도 server, sftp server module, ssh public key 관련 모듈 등이 설치되었다.

![210720163500.png](/assets/images/210720163500.png)

ssh 서버를 동작시킨다.<br>
`service ssh start` 명령어를 통해서 동작을 시키고, `service ssh status` 명령어를 통해서 상태를 확인 한다.

22번 port 를 Listening 하면서 active 상태로 잘 실행되었다.

![210720164144.png](/assets/images/210720164144.png)

`ip addr` 명령어로 VM의 ip를 확인한다. VirtualBox를 이용해 ubuntu를 설치했다면, default로 `10.0.2.15` 라는 내부용 ip가 할당된다.

![210720164345.png](/assets/images/210720164345.png)

VirtualBox에서 해당 서버를 포트포워딩한다.<br>
`설정`->`네트워크`->`고급`->`포트포워딩`

포트 포워딩(Port-Forwarding)이란 컴퓨터 네트워크에서 패킷이 라우터나 방화벽 같은 네트워크 게이트웨이를 통과하는 동안 네트워크 주소를 변환해주는 것을 의미한다.<br>
쉽게 말해 외부에서 접속이 가능하도록 하는 것이다.<br>

[굉장히 쉽게 잘 설명되어 있는 블로그](https://ooeunz.tistory.com/104) 링크를 걸어둔다.

![210720164618.png](/assets/images/210720164618.png)

PuTTY 에서 127.0.0.1 IP를 22번 포트로 접속하면, VM에 SSH서버 10.0.2.15 IP 22번 포트로 접속되는 포트포워딩 Rule을 정의해준다.

- `localhost`는 컴퓨터 네트워크에서 사용하는 루프백 호스트명으로, 자신의 컴퓨터를 의미한다. IPv4에서의 IP 주소는 `127.0.0.1`이며, IPv6에서는 ::1(0:0:0:0:0:0:0:1의 약자)로 변환된다. ([Wiki](https://ko.wikipedia.org/wiki/Localhost))

![210720164714.png](/assets/images/210720164714.png)

대부분 리눅스 계열 서버는 root 접속을 금지하고 있다. 테스트용 로컬 서버이기 때문에 편의를 위해 root 계정 접속을 허용한다.

`apt install vim` 명령어로 vim 편집기를 설치해주고,<br>
`vim /etc/ssh/sshd_config` sshd_config 파일을 수정했다.<br>
파일 내부에서 `/Permit` 과 같이 단어를 검색해서 `PermitRootLogin` 부분 주석을 지우고 뒤에 값을 `yes`로 변경한다.<br>
`:wq!` 명령어로 파일을 저장하면서 빠져나오고,<br>
`service ssh restart` 명령어로 config 파일을 적용시키기위해 ssh server 를 재시작해준다. 

![210720170155.png](/assets/images/210720170155.png)

![210720170338.png](/assets/images/210720170338.png)

이제 PuTTY에 아까 포트포워딩해 둔 IP와 Port를 입력해서 VM으로 SSH 접속한다.

![210720170515.png](/assets/images/210720170515.png)

접속 성공!

![210720170704.png](/assets/images/210720170704.png)

***게스트 확장(VirtualBox Guest Additions) 꼭 설치***

게스트 확장없이는 화면이 작고, 화면도 작고, 화면이 불편하다.<br>
이미 설치해서 캡쳐를 다시 할 순 없고, [참고한 블로그](https://www.manualfactory.net/11071) 링크를 걸어둔다.<br>
굉장히 간단명료한 설명이라 따라하기 편했다.

![210720210609.png](/assets/images/210720210609.png)

이제 드래그앤 드롭으로 해상도조절 및 Host와 Guest 사이의 파일복사, 클립보드 공유 등이 가능하다!!!!

***SSH***

SSH(Secure Shell)는 원격 호스트 컴퓨터에 접속하기 위해 사용되는 인터넷 프로토콜이다. 뜻 그대로 보안 셸이다. 기존의 유닉스 시스템 셸에 원격 접속하기 위해 사용하던 텔넷은 암호화가 이루어지지 않아 계정 정보가 탈취될 위험이 높으므로, 여기에 암호화 기능을 추가하여 1995년에 나온 프로토콜이다. 셸로 원격 접속을 하는 것이므로 기본적으로 CLI 상에서 작업을 하게 된다. 기본 포트는 22번이다.

[참고 : ssh.com - academy](https://www.ssh.com/academy/ssh/command)<br>
[더 공부할 것 : SSH 동작방식, 공개키와 암호키](https://medium.com/@labcloud/ssh-%EC%95%94%ED%98%B8%ED%99%94-%EC%9B%90%EB%A6%AC-%EB%B0%8F-aws-ssh-%EC%A0%91%EC%86%8D-%EC%8B%A4%EC%8A%B5-33a08fa76596)

***VS Code에서 'Remote-SSH' Extention으로 SSH 접속***

Extension 마켓플레이스에서 **Remote - SSH**를 설치한다.

정상적으로 설치되고나면 왼쪽 하단에 `><` 아이콘이 생기고, 왼쪽바 '확장(Extention)' 메뉴 밑에 **'원격 탐색기'** 메뉴가 추가된다.<br>
원격 탐색기 메뉴에서 연결해둔 remote 서버들을 확인할 수 있다.<br> 
원격 탐색기 메뉴에서 `+(Add New)` 버튼을 누르거나 왼쪽 하단 `><`아이콘을 눌러 `Connect to Host` 할 수 있다.<br>

![210720213727.png](/assets/images/210720213727.png)

새로운 Host에 연결할 때는 `ssh` 명령어를 사용하면 된다.

`ssh userName@<hostName 또는 IP> -p <port번호>`

userName에 맞는 pw를 입력하고 VS Code 새 창을 실행해주면, 위에서 열어 둔 ubuntu 서버에 ssh 접속된다.<br>
탐색기를 통해 user의 home 디렉토리가 보인다.<br>

CLI 환경의 장점도 있지만, 역시 GUI 기반의 IDE 환경이 직관적이고 간단하게 사용하기에 더 편한 것 같다.<br>
도대체 VS Code는 어디까지 가능한 것인가...<br>

심지어 document도 잘 되어있다.([VS Code docs - remote ssh](https://code.visualstudio.com/docs/remote/ssh#_getting-started))

![210720211947.png](/assets/images/210720211947.png)

<br>

## Study ShellScript

### **#!/bin/sh**

스크립트의 맨 앞에 나오는 `#!`는 2byte의 매직 넘버(magic number)로 **Shebang(sharp(#) + bang(!))** 이라고 하며, 해당 스크립트를 실행시켜줄 프로그램의 경로를 지정한다.

즉, 쉘스크립트에서 `#!`는 스크립트를 실행할 쉘을 지정하는 선언문이다.<br>
뒤에 나오는 `/bin/sh`는 sh 쉘을 지정해준 것이며 `dash` 쉘을 의미한다.<br>

![210720223430.png](/assets/images/210720223430.png)

쉘 스크립트(`.sh`) 는 기본적으로 `#!/bin/sh`로 시작하는데,<br>
이것은 dash 쉘에서 실행되는 스크립트라고 선언하고 스크립트를 작성하는 것이다.

하지만, `/bin/sh`가 아니라 `/bin/bash`나, (nodejs를 설치했다면)`/usr/bin/node` 도 가능하다.


```sh
#!/bin/sh

echo 'hello world';
```

위와 같은 `hello.sh` 파일을 실행시키면, 내부적으로 `/bin/sh hello.sh` 명령어가 실행되는 것이다.

```sh
#!/usr/bin/node

console.log('hello');
```

위와 같은 `hello.sh` 파일을 실행시키면, `/usr/bin/node hello.sh` 명령어가 실행되는 것이다.

즉, 쉘이 아니더라도 javascript나 python과 같은 interpreter 언어도 **shebang** 사용이 가능하다.

<br>

## Study cron

### **cron, crontab**

- **cron** : unix 계열 운영체제 체제의 시간 기반 job scheduler 데몬 프로세스이다.

`ps -ef | grep cron` 명령어를 이용해 `root` 권한의 `/usr/sbin/cron` 프로세스가 실행 중인 것을 확인할 수 있다.

![210720230139.png](/assets/images/210720230139.png)

cron은 셸 명령어들이 주어진 일정에 주기적으로 실행하도록 규정해놓은 crontab (cron table) 파일에 의해 구동된다. crontab 파일들은 잡 목록 및 cron 데몬에 대한 다른 명령들이 보관된 위치에 저장되어 있다. 사용자들은 자신들만의 개개의 crontab 파일들을 가질 수 있으며, 가끔은 /etc 또는 /etc의 하위 디렉터리에 시스템 관리자들만이 편집할 수 있는, 시스템 전반에 영향을 미치는 crontab 파일이 존재하는 경우도 있다.

- **crontab (cron table)** : cron은 셸 명령어들이 주어진 일정에 주기적으로 실행하도록 규정해놓은 crontab (cron table) 파일에 의해 구동된다. user들은 개개의 crontab 파일들을 가질 수 있다(계정별로 crontab 파일 생성 가능). /etc 하위에 root 권한의 시스템 전반에 영향을 미치는 crontab을 생성할 수도 있다.

[@ click : crontab 작성에 유용한 사이트 @](https://crontab.guru/)

```sh
* crontab 명령어 간단정리

crontab -l : 작업 목록 조회
crontab -e : 작업 목록 편집
crontab -r : 작업 목록 삭제
```

contab 파일을 처음 생성하면 편집기를 선택하고, 주석으로 된 crontab 파일 설명을 볼 수 있다.

![210721004633.png](/assets/images/210721004633.png)<br>
![210721004600.png](/assets/images/210721004600.png)

***cron logging***

redirection을 이용해 cron 실행 결과 log를 남길 수 있다.<br>
만약, 작업 실행 중 오류가 발생해서 작업이 제대로 수행되지 않았을 때, 로그를 남기지 않았다면 디버깅하기 힘들 것이다.

- 덮어쓰기
    
    ```
    * * * * * /home/script/bin/a.sh > /home/script/log/a.sh.log 2>&1
    ```
- 이어쓰기
    
    ```
    * * * * * /home/script/bin/a.sh >> /home/script/log/a.sh.log 2>&1
    ```

***crontab backup***

cron을 이용해 주기적으로 crontab 내용을 백업할 수도 있다.

```
59 23 1 * * crontab -l > /home/script/backup/crontab.bk
```

*cron + 쉘스크립트 파일을 이용하여 서버에서 실행되고 있는 다양한 프로그램들의 log 및 backup 파일들을 일별, 월별로 정리하는데 유용하게 사용할 수 있다.*
*(feat. `tar`, `gz`, `zip`, `cp`, `mv`, `mkdir`...)*

🔎 ***2>&1***

표준 출력이 전달되는 곳으로 표준에러를 출력한다.

- `2` : 표준에러 
- `>` : redirection(리다이렉션, 표준 입출력 스트림 우회)
- `1` : 표준출력
- `&` : 백그라운드 실행

파일디스크립터와 redirection에 대한 더 자세한 내용은 [여기](https://reebok.tistory.com/56)랑 [여기](https://blogger.pe.kr/369) 참고.

<br>

# TIH (Today I Heard)

서버 세팅은 개발자의 기본 중의 기본, 개발의 기초 중의 기초!

<br>

>Reference

- [opentutorials - 생활코딩 : VirtualBox](https://opentutorials.org/course/173)
- [virtualbox - manual : ch01](https://www.virtualbox.org/manual/ch01.html)
- [virtualbox - manual : ch05](https://www.virtualbox.org/manual/ch05.html#vdidetails)
- [[리눅스] ssh란?](https://velog.io/@hyeseong-dev/%EB%A6%AC%EB%88%85%EC%8A%A4-ssh%EB%9E%80)
- [우분투 가상머신 ssh 접속(Ubuntu ssh virtualbox)](https://lts0606.tistory.com/222)
- [VS Code docs - remote ssh](https://code.visualstudio.com/docs/remote/ssh#_getting-started)
- [[Network] Port와 포트 포워딩(Port-Forwarding)이란?](https://ooeunz.tistory.com/104)
- [쉘스크립트(Shell Script) 기초 - Hello world](https://iot-lab.tistory.com/168)
- [[Ubuntu/Linux] #!/bin/sh에 대한 간단한 이야기](https://storycompiler.tistory.com/101)
- [쉘 스크립트(shell script)의 시작 #! 의 뜻](https://ingorae.tistory.com/365)
- [Uinx/Linux: Shebang과 env에 대한 설명 (#!/usr/bin/env)](https://blog.gaerae.com/2015/10/what-is-the-preferred-bash-shebang.html)
- [cron - 위키백과](https://ko.wikipedia.org/wiki/Cron)
- [리눅스 반복 예약 작업 cron, crond, crontab](https://rapperwoo26.tistory.com/30)
- [쉘스크립트에서 이따금씩 사용되는 2>&1 이해하기](https://blogger.pe.kr/369)
- [/dev/null 2>&1 의 의미](https://reebok.tistory.com/56)