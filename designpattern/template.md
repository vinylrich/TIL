# Template
## Template 구현 in golang

---
목차
1. [What is Template](#x란?)
2. [Code](#구현)
3. [Analysis](#코드-분석)
4. [Field of Application](#활용-분야)

___
## x란?
서버는 결국에는 html을 보여주는 용도이다.

붕어빵을 만들 때 붕어빵 틀에 재료를 넣고 앙꼬를 넣는다.

이 붕어빵 틀이 바로 template이라고 할 수 있다.

한 html을 지정하고 그곳에 value를 넣으면 html 틀을 일일이 `<html><body>` 와 같이 넣을 필요가 없다.

아래는 template을 사용했을 때 나오는 출력값이다.
``` html
<html>
<head>
<title>Template</title>
</head>
<body>

Name: junwoo
Email: whktjd0109@gmail.com
Age: 19

<a href="/user?email=whktjd0109%40gmail.com">user</a>        

<script>
var email="whktjd0109@gmail.com"
var name="junwoo"
var age= 19
</script>

Name: 213
Email: wwasd
OldAge:40


<a href="/user?email=wwasd">user</a>

<script>
var email="wwasd"
var name="213"
var age= 40
</script>

</body>
</html>
```

{{.value}}와 같이 값을 지정해주면 틀을 바꿔 원하는 부분에 값을 넣을 수 있다.

___
## 구현

___
## 코드 분석




___
## 활용 분야



