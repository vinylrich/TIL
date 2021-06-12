# GET AND POST


## 개요
GET 방식과 POST 방식 모두 서버에 요청을 하는 HTTP 기본 메서드이다.

요청을 하면 응답을 줘야하는 경우가 발생한다. EX) 웹사이트 상에 올린 글을 다시 불러오기

이 자원을 줘야할 때 GET 방식과 POST 방식 각각 쓰임새가 다르다.
## WHAT IS GET?

클라이언트의 서버로 데이터를 보낼 때 URL 뒤에 보낸다

데이터는 key 와 value형식으로 보내야한다.(Map형식,json형식)

ex)localhost:3000/login/id=junwoo&passwd=1234

URL에 붙이므로, HTTP 헤더에만 포함되어 BODY는 빈 상태가 된다.

BODY DATA를 설명하는 Content-Type은 비게 된다.

### GOLANG에서
url에 포함된 값을 불러올 때
```go
vars := mux.Vars(r)
id, _ := vars["id"]
```
와 같이 받는다
id에는 "junwoo"가 들어갔을 것이다.

### 특징

URL 형태로 표현되므로 다른 사람에게 노출이 쉽다 
(URL 헤더에 덩그러니 아이디와 패스워드를 노출시키면 어떻겠는가?)

또한, 데이터를 보내는 양에 한계가 있다.

___
## What is POST?

POST는 데이터 전송을 주로 한 메서드이다.

POST는 BODY에 데이터를 전송한다.
아까와 똑같은 예제를 활용해보자.

ex)localhost:3000 post
```json
{
    "id":"junwoo",
    "passwd":"1234"
}
```

보내는 형식이 완전히 다르지만, 실제로는 같은 기능을 한다.

BODY의 데이터를 설명하는 Content-Type에 이게 json인지 text/plain인지 html인지 데이터타입을 명시해준다.

### golang에서
```go
    user := new(User)
	err := json.NewDecoder(r.Body).Decode(user) //data받아오기
```
와 같은 형식으로 user structure에 client에서 보내온 data를 받아올 수 있고,
```go
id := r.FormValue("id")
```
와 같이 html에서 보내주는 formvalue를 가져와서 사용하는 방식도 있다.