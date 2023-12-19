---
title: "Maven vs Gradle"
last_modified_at: 2023-12-06
categories:
  - Versus
tags:
  - Maven
  - Gradle
  - TIL
toc: true
toc_sticky: true
toc_label: "TIL"
---

## 더 나은 선택은?

**Maven**과 **Gradle**은 Spring 프로젝트를 개발할 때 사용하는 **빌드 도구**이다. 둘 중에 어떤 것을 사용하는 게 더 나은 선택일까?
결론부터 말하자면 상황에 따라 다르다고 할 수 있는데, 성능만 따지자면 Gradle의 승리다. Gradle은 공식 홈페이지에서 Maven과의 성능 비교 결과를 자랑스럽게 홍보하고 있는데, 해당 내용을 간략하게 정리해보려고 한다.

> 빌드 도구는 빌드 과정을 자동화해주는 역할<br>
여기서 빌드란 작성한 코드를 실행 가능한 애플리케이션으로 패키징하는 것을 의미


> Apache Ant -> Maven -> Gradle 순서로 등장

## Flexibility

구글이 안드로이드 빌드 도구로 Gradle을 선택했다고 하는데, 이는 Gradle의 유연한 확장성때문이라고 한다. C/C++ 네이티브 개발에도 사용할 수 있을 정도로 확장성이 좋은 것 같다.

Maven은 xml로 관리되고, 스크립트가 정형화되어있기 때문에 사용하기 쉽지만 엄격한 규칙때문에 커스텀하기 어렵다는 내용도 있다.

## Perfomance

![image](https://github.com/xkimido/xkimido.github.io/assets/96900790/a9cf81db-b764-48cd-bc07-cb4d384c27c6){: .align-center}

여기서는 빌드 완료까지 걸리는 시간을 비교해준다. Gradle은 캐싱을 지원하기 때문에 캐싱이 완료된 시점에서는 Maven과 굉장한 속도 차이를 보여준다. 아래는 Gradle을 Maven보다 훨씬 빠르게 만들어주는 상위 3가지 기능이다.

- **Incrementality**
    - 번역하니 증분성이라고 한다. Gradle은 작업의 입출력을 추적해서 필요한 작업만 실행한다는 내용이다.
- **Build Cache**
    - 위에서 언급한 캐싱 기능이다. 동일한 입력을 가진 Gradle빌드를 재사용한다고 한다.
- **Gradle Daemon**
    - 빌드 정보를 메모리에 오래 저장할 수 있도록 도와주는 프로세스라는 것 같다. 이 부분은 더 알아봐야겠다...

## User Experience

Maven은 큰 커뮤니티와 오랜 사용 기간으로 아직까지 많은 곳에서 쓰인다. Gradle은 이 부분을 의식하고 사용자들에게 더 다가가기 위해서 Groovy뿐만이 아니라 Kotlin 기반 DSL(Domain Specific Language)을 제공한다.

![image](https://github.com/xkimido/xkimido.github.io/assets/96900790/69f3beb5-3d0e-4f41-b726-917914043a44){: .align-center}

향상된 로깅 및 명령어 자동 완성, `gradle tasks`와 같은 검색 기능을 가지고 있는 최신 CLI를 제공하고, 빌드 디버깅과 최적화를 위한 웹 기반 UI도 제공한다고 한다.

## Dependency Management

Maven도 종속성 관리를 제공하지만 위 내용과 같이 자유도가 떨어진다. Gradle은 사용자 정의가 가능한 부분이 많기 때문에 복잡한 빌드 스크립트를 작성할 수 있다. 여기에서 Gradle이 왜 Flexibility가 좋은지 설명이 되는 것 같다.

## 느낀 점

Maven, Gradle 둘 다 찍먹만 해본 입장에서 "오 그렇구나" 하는 내용도 있었고, 잘 와닿지 않는 내용들도 많았다. 앞으로 여러 프로젝트를 진행하면서 더 깊이 알아가는 시간을 가져야겠다.

## 참고

[Gradle vs Maven Comparison](https://gradle.org/maven-vs-gradle/)

수정이 필요한 부분은 댓글로 피드백 부탁드립니다!
{: .notice--warning}