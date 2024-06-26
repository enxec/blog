---
title: "[Linux] i-node와 파일 링크"
description: 
author: Enxec
date: 2022-08-07
categories: [Linux]
tags: [linux, 리눅스, i-node, 아이노드, 링크, 소프트 링크, 하드 링크, 심볼릭 링크, 링크 명령어]
pin: false
math: true
mermaid: true
image:
  path: /thumbnail/linux-logo.png
  lqip: 
  alt: 
---

리눅스를 공부하다가 심볼릭 링크라는 단어를 접하게되었다. 여러 자료들을 찾아보니 심볼릭 링크는 리눅스의 i-node개념과 연관성이 있는 것을 알게되었고, 이번 포스팅에서 심볼릭 링크를 포함하는 보다 큰 개념인 링크와 이에 연관성을 가지는 i-node에 대해 정리해보고자 한다.

<br>

## i-node
### i-node 개념
리눅스의 파일링크 개념을 이해하려면 i-node를 알아야한다. 리눅스는 파일 시스템을 처리할 때 리눅스 전용 특수한 index를 사용하는데 이것을 i-node라고 한다. i-node는 index-node의 줄임말로, 파일을 빠르게 찾기 위한 노드를 의미하며, 리눅스의 모든 파일에 관한 index정보와 파일정보를 들고 있는 일종의 자료 구조이다.  
때문에 리눅스의 모든 파일 및 디렉토리는 고유한 i-node를 가지고 있으며, 이러한 i-node를 통해 구분이 가능하다.   

즉, i-node는 리눅스에서 파일에 대한 정보(metadata)를 가진, 일종의 데이터라고 이해하면된다.

### i-node 특징
앞전에 i-node는 인덱스 뿐만아니라 파일에 대한 정보(metadata)를 포함하고 있다고 언급하였다. 해당 정보에 대한 목록은 다음과 같다.
- 파일모드(Permission)
- 링크 수
- 소유자명
- 그룹명
- 파일 크기
- 파일 주소
- 마지막 접근 정보
- 마지막 수정 정보
- 아이노드 수정 정보

i-node는 한 파일이 사용하는 모든 블록을 가리키는 포인터들을 포함하는 하나의 블록(데이터 저장 단위)이다. 그래서 i-node는 모든 블록의 주소를 가리키는 포인터들에 대한 정보를 포함하고 있으며, 블록들을 서로 연결하는 역할을 한다.

<br>

## 파일링크란
---
리눅스에서 파일이나 디렉토리를 생성하면 i-node번호가 임의로 부여되고, 이 번호를 기준으로 관리된다. i-node는 'ls -i' 명령으로 확인할 수 있는데, 파일명이 다르더라도 i-node가 같다면 내부적으로는 같은 파일로 인식된다. 이렇게 하나의 파일을 여러 개의 이름으로 관리하거나 디렉토리의 접근 경로를 단축하는 형태를 링크라고 부르고, ln 명령을 통해 만들 수 있다.  

```bash
# 링크 생성 명령어 
ln [원본 파일] [링크 파일]
```

링크는 크게 하드 링크와 심볼릭 링크로 2가지로 나뉜다. 각 링크에 대한 내용은 아래에서 살펴보자.

### 하드링크

![하드 링크](/posts/20220807/hard-link.png "하드 링크"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">하드 링크</div> 

하드 링크는 하나의 동일한 파일을 디스크의 다른 곳에 배치(복사와 같은 형태)하여 여러 이름으로 사용되는 형식이다. 하드 링크는 파일에만 부여할 수 있는데, 리눅스 초기에는 Sticky-Bit가 설정되지 않는 공유 디렉토리에서 사용하였다. 일반적인 공유 디렉토리에 쓰기(w) 권한을 설정하면 누구나 파일을 생성 및 삭제할 수 있게 되는데, 문제는 다른 사용자 소유의 파일도 삭제하는 문제가 발생한다. 이 경우를 대비해서 사용자의 홈 디렉토리 안에 하드링크 파일을 생성해 두면, 다른 사용자에 의해 파일이 삭제되어도 안전하게 보존할 수 있다.

### 심볼릭 링크(소프트 링크)

![심볼릭 링크](/posts/20220807/symbolic-link.png "심볼릭 링크"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">심볼릭 링크</div> 

심볼릭 링크는 소프트 링크라고도 불리며, 하나의 파일을 여러 이름으로 가리키게 하는 것으로 원본과 생성된 링크 파일은 완전히 다른 파일로 관리된다. 파일이나 디렉토리에 모두 사용 가능하나 일반적으로 디렉토리의 경로 단축이나 변경에 사용된다.  
윈도우 시스템에서 제공하는 바로가기 기능과 매우 유사하다. 

### 각 파일링크의 특징
- 하드 링크
  - ls -i 명령으로 i-node 번호를 확인하면 원본과 링크 파일의 번호가 같다.
  - 원본과 링크 파일의 내용과 파일의 크기가 같다.
  - ls -l 명령 시에 출력되는 링크의 숫자가 올라간다.
  - 원본이나 링크 파일 중에 어떠한 파일을 수정해도 같이 반영된다.
  - 원본 파일을 삭제해도 링크 파일은 아무런 영향을 받지 않는다.
  - 하드 링크는 파일만 설정 가능하고, 동일한 파일 시스템에서만 사용 가능하다.
  - 파티션이나 디스크 드라이브를 가로질러 사용할 수는 없다.

- 심볼릭 링크
  - ls -i 명령으로 i-node 번호를 확인하면 원본과 생성된 링크 파일의 번호가 다르다.
  - 생성된 링크 파일의 크기가 매우 작다.
  - ls -l 명령 시에 출력되는 권한 영역의 맨 앞쪽에 'l'이라고 표시된다.
  - 원본이나 링크 파일 중에 어떠한 파일을 수정해도 같이 반영된다.
  - 원본 파일을 삭제하면 링크 파일은 아무런 구실을 하지 못한다.
  - 디렉토리에 링크 파일을 생성하면 윈도우의 바로가기나 단축아이콘의 기능과 같다.
  - 생성되는 링크 파일의 퍼미션 값이 777로 표시되나, 이 값은 원본 파일의 퍼미션과는 무관하다.

### 각 파일링크의 적절한 사용
- 하드 링크
  - 저장공간을 고려할 경우
    >하드 링크 파일은 마치 용량을 점유하고 있는 것처럼 보이지만 진짜로 데이터를 복사한 것이 아니라 이미 존재하는 데이터의 위치만 가리키고 있으며, 별도의 데이터를 저장하지 않기 때문에 용량을 차지하지 않는다. 반면 심볼릭 링크는 자신이 가리키고 있는 파일의 위치를 데이터로서 저장하기 때문에 약간의 용량(보통 4KB)을 차지한다.
  - 성능을 고려할 경우
    >다른 파일을 거치지 않고 직접 디스크 포인터에 액세스하므로 하드 링크로 액세스하면 성능이 좋다.
  - 파일 위치변경을 고려할 경우
    >원본 파일을 같은 파일 시스템의 다른 위치로 옮기면 하드 링크는 계속 작동하지만 소프트 링크는 실패한다.
  - 안정성을 고려할 경우
    >심볼릭 링크보다 하드 링크가 데이터 안전성이 우수하다.
- 심볼릭 링크
  - 파일 시스템에 링크할 경우
  - 디렉토리를 링크할 경우

<br>

## 관련 명령어
### 링크 생성
- 사용법
  - ln [option] 원본 대상파일명
    >옵션을 주지않고 링크 생성 시 하드링크를 생성한다.

- 주요 옵션
  - -s
    >심볼릭 링크를 생성 시에 사용하는 옵션이다.  
    >­­­`--symbolic`­
  - -v
    >링크 만드는 정보를 자세히 출력한다.  
    >­­­`--verbose`
  - -f
    >링크 파일 존재 시에 삭제하고 생성한다.  
    >­­­`--force`

- 사용 예

```bash
# won.txt라는 파일의 하드링크 파일인 w를 
# 현재 위치하는 디렉토리에 생성
ln won.txt w
```
```bash
# won.txt라는 파일의 심볼릭 링크 파일인 w를 
# 현재 위치하는 디렉토리에 생성
ln -s won.txt w
```
```bash
# /etc/xinetd.d의 심볼릭 링크 파일인 w를 
# 현재 위치하는 디렉토리에 생성
ln -s /etc/xinetd.d w
```

---

읽어주셔서 감사합니다. 😊

__Reference__  
[[Linux] 리눅스 시스템의 아이노드(inode), 심볼릭 링크(Symbolic Link), 하드 링크(Hard Link)에 대해서. - Tistory](https://i5i5.tistory.com/341)  
[심볼릭 링크란 무엇일까 - Tistory](https://haruhiism.tistory.com/18)  