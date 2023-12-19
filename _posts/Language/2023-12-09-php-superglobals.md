---
title: "PHP Superglobals"
last_modified_at: 2023-12-10
categories:
  - Language
tags:
  - PHP
toc: true
toc_sticky: true
toc_label: "PHP Superglobals"
---

# Built-in variables

## superglobals

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

## $GLOBALS

전역 변수에 대한 참조를 포함하는 연관 배열

> 연관 배열은 키 하나와 값 하나가 연관되어 있으며, 키를 통해 연관되는 값을 얻을 수 있다.<br>
흔히 사용하는 Map을 생각하면 될 것 같다.

```php
<?php
function test() {
    $foo = "local variable";

    echo '$foo in global scope: ' . $GLOBALS["foo"] . "\n";
    echo '$foo in current scope: ' . $foo . "\n";
}

$foo = "Example content";
test();
?>

/*
$foo in global scope: Example content
$foo in current scope: local variable
*/
```

PHP 8.1.0 버전부터는 $GLOBALS의 쓰기 권한을 지원하지 않는다.<br>
따라서 아래 예제와 같이 사용하게 되면 컴파일 에러를 만난다.
{: .notice--danger}

```php
<?php
 // Generates compile-time error:
 $GLOBALS = [];
 $GLOBALS += [];
 $GLOBALS =& $x;
 $x =& $GLOBALS;
 unset($GLOBALS);
 array_pop($GLOBALS);
 // ...and any other write/read-write operation on $GLOBALS
 ?>
```

## $_SERVER

헤더, 경로, 스크립트 위치 등의 정보를 포함하는 연관 배열이다.<br>
이 배열의 항목은 웹 서버에 의해 생성된다고 한다.

```php
<?php
echo $_SERVER['SERVER_NAME'];
?>
```

## $_GET

form 요소를 통해 입력된 값을 연관 배열로 받는다.<br>
GET요청 뿐만 아니라 쿼리스트링이 포함된 모든 요청을 받는다.

```php
<?php
echo 'Hello ' . htmlspecialchars($_GET["name"]) . '!';
?>

/*
Hello param!
*/
```

## $_POST

HTTP Content-Type으로 `application/x-www-form-urlencoded` 또는 `multipart/form-data`를 사용할 때<br>
POST 메서드를 통해 전달되는 변수의 연관 배열이다.

```php
<?php
echo 'Hello ' . htmlspecialchars($_POST["name"]) . '!';
?>

/*
Hello param!
*/
```

## $_FILES

업로드된 파일의 모든 정보가 포함된다.

- $_FILES['userfile']['name']
- $_FILES['userfile']['type']
- $_FILES['userfile']['size']
- $_FILES['userfile']['tmp_name']
- $_FILES['userfile']['error']
- $_FILES['userfile']['full_path']

### Validating file uploads

```php
<?php
$uploaddir = '/var/www/uploads/';
$uploadfile = $uploaddir . basename($_FILES['userfile']['name']);

echo '<pre>';
if (move_uploaded_file($_FILES['userfile']['tmp_name'], $uploadfile)) {
    echo "File is valid, and was successfully uploaded.\n";
} else {
    echo "Possible file upload attack!\n";
}

echo 'Here is some more debugging info:';
print_r($_FILES);

print "</pre>";

?>
```

### Uploading array of files

```html
<form action="" method="post" enctype="multipart/form-data">
  <p>Pictures:
    <input type="file" name="pictures[]" />
    <input type="file" name="pictures[]" />
    <input type="file" name="pictures[]" />
    <input type="submit" value="Send" />
  </p>
</form>
```

```php
<?php
foreach ($_FILES["pictures"]["error"] as $key => $error) {
    if ($error == UPLOAD_ERR_OK) {
        $tmp_name = $_FILES["pictures"]["tmp_name"][$key];
        // basename() may prevent filesystem traversal attacks;
        // further validation/sanitation of the filename may be appropriate
        $name = basename($_FILES["pictures"]["name"][$key]);
        move_uploaded_file($tmp_name, "data/$name");
    }
}
?>
```

## $_COOKIE

쿠키를 통해 전달되는 값의 연관 배열이다.

```php
<?php
echo 'Hello ' . htmlspecialchars($_COOKIE["name"]) . '!';
?>

/*
Hello param!
*/
```

## $_SESSION

세션 변수의 연관 배열이다.

```php
<?php
// page1.php

session_start();

echo 'Welcome to page #1';

$_SESSION['favcolor'] = 'green';
$_SESSION['animal']   = 'cat';
$_SESSION['time']     = time();

// Works if session cookie was accepted
echo '<br /><a href="page2.php">page 2</a>';

// Or maybe pass along the session id, if needed
echo '<br /><a href="page2.php?' . SID . '">page 2</a>';
?>
```

## $_REQUEST

`$_GET` `$_POST` `$_COOKIE`를 기본으로 포함하는 연관 배열이라고 한다.

## $_ENV

환경변수의 연관 배열이다. `admin`이라는 유저가 스크립트를 실행한다면 아래와 같은 결과가 나온다.

```php
<?php
echo 'My username is ' .$_ENV["USER"] . '!';
?>

/*
My username is admin!
*/
```

## 참고

[Superglobals](https://www.php.net/manual/en/language.variables.superglobals.php)<br>
[Session Functions](https://www.php.net/manual/en/ref.session.php)

수정이 필요한 부분은 댓글로 피드백 부탁드립니다!
{: .notice--warning}