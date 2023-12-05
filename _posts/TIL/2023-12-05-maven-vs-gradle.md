---
title: "Maven vs Gradle"
last_modified_at: 2023-12-05
categories:
  - TIL
toc: true
toc_sticky: true
toc_label: "TIL"
---

## 더 나은 선택은?

Maven과 Gradle은 Spring 프로젝트를 개발할 때 사용하는 **빌드 도구**이다. 둘 중에 어떤 것을 사용하는 게 더 나은 선택일까?
결론부터 말하자면 상황에 따라 다르다고 할 수 있는데, 성능만 따지자면 Gradle의 승리다.

> 빌드 도구는 빌드 과정을 자동화해주는 역할<br>
여기서 빌드란 작성한 코드를 실행 가능한 애플리케이션으로 패키징하는 것을 의미

초기에는 `Apache Ant`라는 빌드 도구를 사용했는데, 많은 스크립트 작성과 부족한 의존성 관리로 인해 `Maven`이 나오게 된다. 그리고 xml이 아닌 Groovy 언어를 기반으로 스크립트를 구축하는 `Gradle`이 등장한다.