---
layout: "single"
title: "2021.07.22 TIL (Today I Learned)"
categories: ['Programming','TIL','BoostCamp-Challenge']
tags: ['Memory Structure','Process Memory Model','Node.js Memory Model','GC','GarbageCollector']
permalink : /TIL/day4
---
# TIL (Today I Learned)
**BoostCamp Challenge DAY-4**

- Study Process Memory Model
- Study Node.js Memory Model
- Study GarbageCollector

## Study Process Memory Model

### Program vs Process

- 프로그램(Program) : 컴퓨터를 실행시키기 위한 일련의 순차적으로 작성된 명령어의 모음. 컴퓨터 시스템의 disk와 같은 secondary storage에 바이너리 형태로 저장되어 있다.
- 프로세스(Process) : 실행되고 있는 프로그램의 추상화(abstraction). disk에 있던 프로그램을 메모리에 적재하여 운영체제의 제어를 받는 상태의 프로그램을 말한다. 
    - **주소공간(Address Space)** : 프로세스가 차지하는 메모리 공간. Protection Domain (서로의 주소 공간을 침범할 수 없음)

![210723095126.png](/assets/images/210723095126.png)

### 메모리 구조

프로그램이 실행되기 위해서는 먼저 프로그램이 메모리에 로드(load)되어야 한다.
또한, 프로그램에서 사용되는 변수들을 저장할 메모리도 필요하다.

프로그램이 운영체제로부터 할당받는 대표적인 메모리 공간은 다음과 같다. (Address Space)

![210723095308.png](/assets/images/210723095308.png)

### IPC (Inter-Process Communication)

- 목적 
    - 정보 공유 (Information sharing) : 여러 프로세스가 동일한 정보에 동시에 access 할 수 있다.
    - 계산 속도 향상 (Computer speedup) : 특정 작업을 빠르게 실행하기위해 각 작업을 sub-tasks로 나눌 필요가 있다. sub-tasks가 병렬(parallel)로 실행되기 위해서 각 sub-tasks 사이에 communication이 필요하다.
    - 모듈화 (Modularity) : 프로세스나 쓰레드를 분할하여 시스템을 모듈 방식으로 구축할 수 있다. 
    - 편의성 (Convenience) : 단일 사용자가 한 번에 여러 개의 작업을 할 수 있다.

- IPC Basic 모델

![210723081918.png](/assets/images/210723081918.png)

(a) Message passing 
- 커널에서 message queue와 system call을 이용하여 프로세스들 간에 메세지를 교환한다.
- 작은 양의 데이터를 교환하는 데 유용하다.
- shared memory model에 비해 구현하기가 쉽지만 느리다.

(b) Shared memory 
- shared-momory 영역을 할당하여 프로세스들이 함께 사용한다. 
- Message passing에 비해 빠르다.
    - 처음 shared-momory region을 차지할 때에만 System call이 한 번 필요하며, 일단 메모리 영역을 차지하고 나면, 이후는 일반적인 메모리 접근과 같다. 
    - 메모리 접근 방식은 프로세스에서 설정되며 운영체제가 개입하지 않는다.

<br>

## Study Node.js Memory Model

### Memory Model

Java가 JVM에 의해 컴파일되고 실행된다면(Runtime), 인터프리터 언어인 Javascript는 
Node.js의 V8엔진이 Javascript를 해석하고 컴파일하여 기계어로 변환하다.

V8은 C++로 작성되었으며 C++ 어플리케이션에서 내장할 수 있다.

#### Resident Set

Javascript는 단일 스레드이므로 컨텍스트 당 하나의 프로세스를 사용한다. 프로세스 당 할당받은 메모리를 Resident Set이라고 한다.

![210723101537.png](/assets/images/210723101537.png)

### Memory Leak



<br>

## 😥 NOT DONE
- Resident Set
- GarbageCollector
- Memory Leak

<br>

# TID (Today I Decided)

주말에 꼭 JavsScript 마스터(?) 해야지...

<br>

>Reference

- [Toast - V8 엔진(자바스크립트, NodeJS, Deno, WebAssembly) 내부의 메모리 관리 시각화하기](https://ui.toast.com/weekly-pick/ko_20200228)
- [Pointers and dynamic memory - stack vs heap](https://www.youtube.com/watch?v=_8-ht2AKyH4&list=LL&index=5&t=11s&ab_channel=mycodeschool)
- [TCP Schiil - memory structure](http://tcpschool.com/c/c_memory_structure)
- [W3 Schools - operating system tutorial - IPC](https://www.w3schools.in/operating-system-tutorial/interprocess-communication-ipc/)
- [프로세스란 무엇인가](https://www.google.com/search?q=%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EB%9E%80&tbm=isch&ved=2ahUKEwjilISF-ffxAhXpw4sBHe0QDhcQ2-cCegQIABAA&oq=%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EB%9E%80&gs_lcp=CgNpbWcQAzICCAAyAggAMgIIADICCAAyAggAMgIIADICCAAyAggAMgIIADICCAA6CAgAELEDEIMBOgQIABADOgUIABCxAzoECCMQJ1CDoAlY9KgJYM-pCWgAcAB4AIABlwGIAegIkgEEMC4xMJgBAKABAaoBC2d3cy13aXotaW1nwAEB&sclient=img&ei=jg76YOKVK-mHr7wP7aG4uAE&bih=782&biw=1474#imgrc=q9ZnPFeATjzUVM)
- [OS#1. 운영체제 구조](https://devowen.com/215)