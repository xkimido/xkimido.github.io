---
title: "PHP Superglobals"
last_modified_at: 2023-12-10
categories:
  - TIL
tags:
  - PHP
toc: true
toc_sticky: true
toc_label: "TIL"
---

## Built-in variables

PHP는 미리 정의된 전역 변수 `superglobals`을 제공한다.
특별한 선언 없이 스크립트 내에서 바로 사용 가능하다.

1. $GLOBALS
2. $_SERVER
3. $_GET
4. $_POST
5. $_FILES
6. $_COOKIE
7. $_SESSION
8. $_REQUEST
9. $_ENV

## 참고

[Superglobals](https://www.php.net/manual/en/language.variables.superglobals.php)

**TIL**은 처음 알게 된 내용을 가볍게 정리한 글입니다.<br>
수정이 필요한 부분은 댓글로 피드백 부탁드립니다!
{: .notice--warning}