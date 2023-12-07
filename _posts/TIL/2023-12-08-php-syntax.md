---
title: "PHP Syntax"
last_modified_at: 2023-12-08
categories:
  - TIL
tags:
  - PHP
toc: true
toc_sticky: true
toc_label: "TIL"
---

# PHP 문법

## 코드 영역 지정

```php
// PHP 권장 스타일
<?php ... ?>

// HTML 스크립트 스타일
<script language = "php"> ... </script>

// SGML 스타일
<? ... ?>

// ASP 스타일
<% ... %>
```

> **SGML**과 **ASP** 스타일은 `php.ini` 설정 파일의 특정 태그를 활성화했을 경우에만 인식된다고 한다.<br>
서버별 이식성 문제 등을 방지하기 위해 PHP 권장 스타일을 사용하는 것이 좋다.

## 기본 문법

```php
// 1. 명령문은 세미콜론으로 끝남
<?php
    echo "PHP Syntax TIL";
?>

// 2. 코드 종료시 세미콜론을 자동으로 붙여주기 때문에 아래 예제도 정상 동작
<?php
    echo "PHP Syntax TIL"
?>

// 3. 종료 태그 생략 가능
<?
    echo "PHP Syntax TIL";
```

> 가독성을 고려해서 세미콜론과 종료 태그는 모두 사용하는 것이 좋다.

### 변수

```php
$name = value;
```

### 상수

```php
const NAME = value;

// 상수 정의
define('NAME', value);
```

## 주석

```php
# 주석문
// 주석문
/* 주석문(여러 줄 가능) */
```

> 여러 줄 주석 안에 한 줄 주석은 삽입할 수 있지만, 여러 줄 주석 안에 중첩하여 사용하면 안 된다.

## echo() 함수

`echo()`는 사실 함수가 아니다. (!?) 출력을 위해 존재하는 하나의 문법이다.<br>
그래서 인수를 전달할 때 괄호를 생략할 수도 있고, 가변 길이로 사용할 수도 있다.<br>

```php
<?php
    echo "괄호 생략";
    echo ("괄호 사용");
    ECHO "echo() 함수의 키워드는 대소문자를 구분하지 않는다.";
    echo "첫 번째 인수, ", "두 번째 인수";
    // echo("첫 번째 인수, ", "두 번째 인수"); // 오류 발생
?>
```

> PHP는 키워드, 클래스, 함수, 사용자 함수 이름의 대소문자를 구분하지 않는다.

## 참고

[https://tcpschool.com/php/intro](https://tcpschool.com/php/php_intro_syntax)

**TIL**은 처음 알게 된 내용을 가볍게 정리한 글입니다.<br>
수정이 필요한 부분은 댓글로 피드백 부탁드립니다!
{: .notice--warning}