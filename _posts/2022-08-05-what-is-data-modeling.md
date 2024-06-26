---
title: "[SQL] 데이터 모델링에 대하여"
description: 
author: Enxec
date: 2022-08-05
categories: [Language, SQL]
tags: [sql, 데이터 모델, 데이터 모델링, data model, data modeling]
pin: false
math: true
mermaid: true
image:
  path: /thumbnail/sql-logo.png
  lqip: 
  alt: 
---

프로그램을 설계할 때 중요한 요소들이 다양하게 존재한다. 그 중에서도 각별히 신경쓰고 많은 시간과 노력을 투자하는 요소 중 하나가 데이터 모델링이다.  
데이터 모델링은 최초에 어떻게 설계하여 가져가느냐에 따라 개발 프로세스에 막대한 영향을 끼친다. 지금부터 프로그래밍에 막대한 영향을 미치는 이 데이터 모델링이라는 것이 대체 무엇인지 자세히 알아보자.

<br>

## 모델링의 이해
### 모델링의 정의
인류의 가장 보편적인 특징이면서 욕구 중 하나는 의사소통을 하며 기록을 남기는 것이며, 이것을 바탕으로 효율성을 극대화하여 사람이 어떠한 목적을 달성하기 위해 고급화한 표현 방법으로 등장한것이 모델이다. 이러한 모델을 만들어가는 그 자체를 모델링이라고 하며, 사람이 살아가면서 접할 수 있는 다양한 현상을 표기법에 따라 표기하는 것 그 자체를 의미한다.  

모델링의 다양한 정의는 다음과 같다.
- 웹스터 사전
  >가설적 또는 일정 양식에 맞춘 표현  

  >어떤 것에 대한 예비표현으로 그로부터 최종 대상이 구축되도록 하는 계획으로서 기여하는 것

- 복잡한 '현실세계'를 단순화해 표현하는 것
- 사물 또는 사건에 관한 양상이나 관점을 연관된 사람이나 그룹을 위하여 명확하게 하는 것
- 현실세계를 추상화한 반영

### 모델링의 특징
모델링의 특징은 크게 3가지로 요약할 수 있다.
- 추상화
  >현실세계를 일정한 형식에 맞추어 표현한다는 의미로 정리할 수 있다. 즉, 다양한 현상을 일정한 양식인 표기법에 따라 표현하는 것이다.
- 단순화
  >복잡한 현실세계를 약속된 규약에 의해 제한된 표기법이나 언어로 표현하여 쉽게 이해할 수 있도록 하는 개념을 의미한다.
- 명확화
  >누구나 이해하기 쉽게 대상에 대한 애매모호함을 제거하고 정확하게 현상을 기술하는 것을 의미한다.

위와 같은 특징을 바탕으로 모델링은 다시 정의하면 '현실세계를 추상화, 단순화, 명확화하기 위해 일정한 표기법에 의해 표현하는 기법'이라 할 수 있다.

### 모델링의 3가지 관점
모델링은 크게 3가지 관점으로 구분하여 바라 볼 수 있다.

![모델링의 관점](/posts/20220805/modeling-aspect.png "모델링의 관점"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">모델링의 관점</div> 

- 데이터 관점
  >업무가 어떤 데이터와 관련이 있는지 또는 데이터 간의 관계는 무엇인지에 대해서 모델링하는 방법
- 프로세스 관점
  >실제하고 있는 업무는 무엇인지 또는 무엇을 해야 하는지를 모델링하는 방법
- 데이터와 프로세스의 상관 관점
  >업무가 처리하는 일의 방법에 따라 데이터는 어떻게 영향을 받고 있는지 모델링하는 방법

<br>

## 데이터 모델의 기본 개념 이해
### 데이터 모델링의 정의
데이터 모델은 DB의 골격을 이해하고 이해한것을 바탕으로 SQL문장을 기능과 성능적인 측면에서 효율적으로 작성하기 위해 꼭 알아야 하는 핵심요소이다. DB의 논리적인 구조, 즉 데이터 모델을 이해하는 것은 SQL 문장을 어떻게 구성할지에 대한 지식과 효율적인 구성에 대한 밑바탕의 지식을 쌓기 위한 핵심 이론이라고 할 수 있다.  

데이터 모델링의 정의는 다음과 같다.
- 정보 시스템을 구축하기 위한 데이터 관점의 업무 분석 기법
- 현실세계의 데이터에 대해 약속된 표기법에 의해 표현하는 과정
- DB를 구축하기 위한 분석 및 설계의 과정

### 데이터 모델이 제공하는 기능
업무분석 관점에서 데이터 모델이 제공하는 기능은 다음과 같다.
- 시스템을 현재 또는 원하는 모습으로 가시화
- 시스템의 구조와 행동을 명세화
- 시스템을 구축하는 구조화한 틀을 제공
- 시스템 구축과정에서 결정한 것을 문서화
- 다양한 영역에 집중하기 위해 다른 영역의 세부사항은 숨기는 다양한 관점을 제공
- 특정 목표에 따라 구체화한 상세 수준의 표현방법 제공

<br>

## 데이터 모델링의 중요성과 유의점
### 데이터 모델링의 중요성
데이터 모델링이 중요한 이유는 다음과 같다.
- 파급효과
  >시스템 구축이 완성되어 가는 시점에서 많은 애플리케이션들의 테스트를 수행하고 대규모 데이터 이행을 성공적으로 수행하기 위한 많은 단위 테스트들이 반복된다. 각 단위 테스트들이 성공적으로 완료되면 이 전체를 묶어 병행 테스트와 통합 테스트를 하게 된다. 만약 이러한 시점에서 데이터 모델의 변경이 불가피해지는 상황이 주어진다고 가정해보자. 이를 위해 데이터 구조 변경에 따른 영향 분석이 일어난다. 그 이후에는 해당 변경 작업이 이루어지는데, 이때 전체 프로젝트에 막대한 영향을 끼치게되는 모델변경이라면 큰 위험요소가 아닐 수 없다. 따라서 시스템 구축 작업 중 다른 어떠한 설계 과정보다 데이터 설계가 중요하다고 볼 수 있다.
- 복잡한 정보 요구 사항의 간결한 표현
  >데이터 모델을 구축할 시스템의 정보 요구 사항과 한계를 가장 명확하고 간결하게 표현할 수 있는 도구다. 또한 데이터 모델은 시스템을 구축하는 많은 관련자가 설계자의 생각대로 정보 요구 사항을 이해하고 이를 운용할 수 있는 애플리케이션을 개발하고, 데이터 정합성을 유지하는 것이다. 이렇게 이상적으로 역할을 할 수 있는 모델이 갖추어야 할 가장 핵심은 정보 요구 사항이 정확하고 간결하게 표현되어야 한다는 것이다.
- 데이터 품질
  >DB에 담겨 있는 데이터는 기업의 중요자산이며 기간이 오래되면 될수록 활용가치가 올라간다. 그런데 이러한 데이터가 만약 정확성과 가치가 떨어지는 데이터라면 얘기가 달라진다. 이것은 해당 데이터로 소중한 비즈니스의 기회상실로 연결된다. 데이터 품질의 중요성은 이점에서 대두된다. 데이터는 오랜기간 숙성되어 전략적으로 활용될때 그 가치는 빛을 바라는데, 품질이 떨어지는 데이터를 오랜기간 보유하고 있었다면 여러 방면에서 타격이 크다. 그럼 데이터 그 자체가 문제였던 것일까? 아니다. 보통 데이터품질의 문제를 야기시키는 가장 큰 원인은 데이터 구조이다. 예를 들어 중복 데이터의 미정의, 데이터 구조에서 비즈니스 정의 불충분 등의 이유로 데이터 품질 문제를 바로잡는 것이 불가능한 경우가 대부분이다.

### 데이터 모델링의 유의점
- 중복
  >데이터 모델은 같은 데이터를 사용하는 사람, 시간, 장소를 파악하는데 도움을 준다. 이러한 지식 응용은 데이터베이스가 여러 장소에 같은 정보를 저장하는 잘못을 하지 않도록 한다.
- 비유연성
  >데이터 모델을 어떻게 설계하였느냐에 따라 사소한 업무 변화에도 데이터 모델이 수시로 변경됨으로써 유지보수의 어려움을 가중시킬 수 있다. 데이터의 정의를 데이터의 사용 프로세스와 분리함으로써 데이터 모델링은 데이터 혹은 프로세스의 작은 변화가 애플리케이션과 DB에 중대한 변화를 일으킬 가능성을 줄인다.
- 비일관성
  >데이터의 중복이 없더라도 비일관성은 발생한다. 예를 들어 신용 상태에 대한 갱신 없이 고객의 납부 이력 정보를 갱신하는 것이다. 개발자가 다른 데이터와 모순된다는 고려 없이 일련의 데이터를 수정할 수 있기 때문이다. 따라서 데이터 모델링을 할 때 데이터와 데이터 간 상호 연관 관계에 대한 명확한 정의는 이러한 위험을 사전에 예방할 수 있도록 돕는다.

<br>

## 데이터 모델링의 3단계 진행
---
데이터 모델은 데이터베이스를 만들어내는 설계서로서 분명한 목표를 가지고 있다. 현실세계에서 DB까지 만들어지는 과정은 아래 그림과 같다.

![모델링 프로세스](/posts/20220805/modeling-process.png "모델링 프로세스"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">모델링 프로세스</div> 

위 그림을 보면 알 수 있듯이 데이터 모델링은 추상화 수준에 따라 3단계로 나뉘어 진행된다.
- 개념적 데이터 모델링
  >추상적 수준이 높고 구체적 수준은 낮으며, 업무 중심적으로 포괄적인 수준의 모델링을 진행하는 것이다. 전 조직에 걸쳐 이루어진다면 '전사적 데이터 모델링' 이라고도 하며, EA 수립 시 많이 이용된다.
- 논리적 데이터 모델링
  > 추상적 수준과 구체적 수준이 보통이며, 시스템으로 구축하고자 하는 업무에 대해 Key, 속성, 관계 등을 정확하게 표현하고 재사용성이 높다.
- 물리적 데이터 모델링
  >추상적 수준이 낮고 구체적 수준이 높으며, 실제로 DB에 이식할 수 있도록 성능, 및 저장 등 물리적인 성격을 고려하여 설계한다.

<br>

## 프로젝트 생명주기에서 데이터 모델링
---
일반적으로는 계획 또는 분석단계에서 개념적 데이터 모델링, 분석 단계에서 논리적 데이터 모델링, 설계 단계에서 물리적 데이터 모델링이 수행된다. 단 현실 프로젝트에서는 개념적 데이터 모델이 생략된 개념 및 논리 데이터 모델링이 분석 단계 때 대부분 수행된다.

![프로젝트 생명주기에 따른 데이터 모델](/posts/20220805/data-model-according-to-project-lifecycle.png "프로젝트 생명주기에 따른 데이터 모델"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">프로젝트 생명주기에 따른 데이터 모델</div>

데이터 축과 애플리케이션 축으로 구분하여 프로젝트를 진행하면서 각각에 도출한 사항은 상호 검증을 지속적으로 수행하면서 단계별 완성도를 높여간다. 단 객체지향 개념은 데이터와 프로세스를 한꺼번에 바라보면서 모델링을 전개하므로 데이터 모델링과 프로세스 모델링을 구분하지 않고 일체형으로 진행하게 된다.

<br>

## 데이터 모델링에서 데이터 독립성 이해
### 데이터 독립성의 필요
데이터 독립성을 이해하기 위해선 데이터 독립성 개념의 출현 배경을 이해해야한다. 출현 배경에는 여러 요소들이 있겠지만 그중 몇가지를 고른다면 다음과 같다.
- 유지보수 비용증가
- 데이터 복잡도 증가
- 데이터 중복성 증가
- 요구사항 대응 저하

위와 같은 이유로 데이터 독립성을 확보하면 아래와 같은 효과를 얻을 수 있다.
- 각 뷰의 독립성을 유지하고 계층별 뷰에 영향을 주지 않고 변경할 수 있다.
- 단계별 스키마에 따라 DDL과 DML이 다름을 제공한다.

### DB 3단계 구조
ANSI/SPARC의 3단계 구성의 데이터 독립성 모델은 외부 단계와 개념적 단계, 내부적 단계로 구성된 서로 간섭되지 않는 모델을 제시하고 있다.

![데이터 독립성](/posts/20220805/data-independence.png "데이터 독립성"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">데이터 독립성</div>

- 외부 단계
  >사용자와 가까운 단계로, 사용자 개개인이 보는 자료에 대한 관점과 관련이 있는 부분이다. 즉, 사용자가 처리하고자 하는 데이터 유형·관점·방법에 따라 다른 스키마 구조를 가지고 있다.
- 개념 단계
  >사용자가 처리하는 데이터 유형의 공통적인 사항을 처리하는 통합된 뷰를 스키마 구조로 디자인한 형태다. 우리가 쉽게 이해하는 데이터 모델은 사용자가 처리하는 통합된 뷰를 설계하는 도구로 이해해도 무방하다.
- 내부적 단계
  >데이터가 물리적으로 저장된 방법에 대한 스키마 구조를 말한다.

위 3단계 구조의 상세 사항을 구성별로 표로 작성하면 다음과 같다.

![데이터 독립성 구성요소](/posts/20220805/data-independence-components.png "데이터 독립성 구성요소"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">데이터 독립성 구성요소</div>

### 두 영역의 데이터 독립성
앞전에 언급한 DB 3단계로 개념이 분리되면서 각각의 영역에 대한 독립성을 지정하는 용어가 논리적인 독립성과 물리적인 독립성이다.

![논리적·물리적 데이터 독립성](/posts/20220805/logical-pysical-independence.png "논리적·물리적 데이터 독립성"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">논리적·물리적 데이터 독립성</div>

### 사상
사상은 영어로 Mapping이다. 이것은 상호 독립적인 개념을 연결시켜주는 다를 뜻하며, 데이터 독립성에서는 크게 2가지 사상이 도출된다.

![사상](/posts/20220805/mapping.png "사상"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">사상</div>

<br>

## 데이터 모델링의 요소
### 데이터 모델링의 3가지 중요 요소
데이터 모델링을 구성하는 중요한 요소 3가지는 다음과 같다.
- 업무가 관여하는 어떤것(Things)
- 어떤 것이 가지는 성격(Attributes)
- 업무가 관여하는 어떤 것 간의 관계(Relationships)

이 3가지는 데이터 모델링을 완성해 가는 핵심 개념으로서 결국 엔터티, 속성 관계로 인식되는 것이다.

### 단수와 복수의 명명
데이터 모델링에서는 위에서 언급한 3가지 중요 요소에 대해 단수와 복수의 개념을 분명하게 구분하고 있고 실제로 데이터 모델링을 할 때 많이 활용한다.  

각 요소에 대한 단수 및 복수의 명명은 다음과 같다.

![단수와 복수의 명명](/posts/20220805/singular-plural-nomenclature.png "단수와 복수의 명명"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">단수와 복수의 명명</div>

<br>

## 데이터 모델링의 이해관계자
---
실제 업무 시스템을 구축하는 실적 프로젝트에서는 DB를 전문적으로 하는 DBA가 데이터 모델링을 전적으로 하는 예는 거의 없다. 오히려 업무 시스템을 개발하는 응용 시스템 개발자가 데이터 모델링까지 하게된다. 이유는 데이터 모델링이라는 과정이 단지 DB를 설계한다는 측면보다 업무를 이해하고 분석하여 표현하는 것이 중요하고, 표현된 내용을 바탕으로 프로젝트 관련자와 의사소통하고 프로그램이나 다른 표기법과 비교 검증하는 일을 수행하는 등 많은 시간을 업무분석과 설계에 할애하기 때문이다. 이에 따라 업무 영역별 개발팀에서 보통 데이터 모델링을 진행하게 된다. 물론 대형 시스템이라면 모델링만을 전문적으로 담당하는 모델러를 투입하여 진행하는 경우도 있지만, 이와 같은 경우도 실제 모델링 작업은 응용 프로그램을 개발하는 사람이나 업무 분석가가 담당한다. 모델러나 DBA는 정확하게 모델링이 진행될 수 있도록 교육하고 제시하며 현안별로 직접 모델링하는 역할을 수행한다.

![데이터 모델 이해관계자](/posts/20220805/data-model-stakeholder.png "데이터 모델 이해관계자"){: width="100%"}
<div style="color: gray; text-align: center; margin-bottom: 30px;">데이터 모델 이해관계자</div>

<br>

## 좋은 데이터 모델의 요소
---
일반적으로 시스템 구축과정에서 생성되는 데이터 모델은 그 품질 평가가 매우 어렵다. 특정 데이터 모델이 업무 환경에서 요구하는 사항을 얼마나 잘 시스템적으로 구현할 수 있는가를 객관적으로 평가할 수 있다면 이것이 가장 좋은 평가 방법일 것이다. 하지만 어디에도 이것을 객관적으로 평가할 수 있는 기준이 존재하지 않는다는 것이 현실이다.  
이러한 상황속에 대체적으로 좋은 데이터 모델이라고 말할 수 있는 몇 가지가 요소들이 존재하며 내용은 다음과 같다.

- 완전성
  >업무에 필요로 하는 모든 데이터가 정의된 모델
- 중복 배제
  >하나의 DB내에 동일한 사실은 반드시 한번만 기록된 모델
- 업무 규칙
  >데이터 모델링 과정에서 도출되고 규명되는 수많은 업무 규칙을 데이터 모델에 표현하고 이를 해당 데이터 모델로 활용하는 모든 사용자가 공유할 수 있도록 제공되는 모델
- 데이터 재사용
  >데이터의 통합성과 독립성에 대해 충분히 고려하여 데이터 재사용성을 제고하는 모델
- 의사소통
  >정보시스템을 운용 및 관리하는 많은 관련자들이 설계자가 정의한 많은 업무 규칙들을 받아들이고 활용할 수 있게 제시되는 모델
- 통합성
  >공유 데이터에 대한 구조를 여러 업무 영역에서 공동으로 사용하기 용이하게 설계한 모델

---

읽어주셔서 감사합니다. 😊

__Reference__  
SQL 전문가 가이드 - Kdata 한국데이터산업진흥원  
[데이터 모델의 이해 - dataonair](https://dataonair.or.kr/db-tech-reference/d-guide/sql/?mod=document&uid=330)