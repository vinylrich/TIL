# http.Handlefunc 와 http.Handle의 차이

## Handlefunc
### 정의:미리 선언된 객체가 없는 상태로 함수를 사용해서 다이렉팅 하는 방법
#### 코드예제
```
http.Handlefunc("/Handlefunc", func(w http.ResponseWriter, r *http.Request){
    fmt.Fprint("hello Handlefunc")
})
```
보이는데로 함수 안에 함수를 사용해 바로 정의한다.

## Handle
### 정의:미리 객체를 선언해 함수를 끌어와 쓰는 방법
#### 코드예제
```
type LoginHandler struct{}

func(l *LoginHandler) ServeHTTP{
    fmt.Fprint("Hello Handle")
}

http.Handle("/Handle",&Loginhandler{})
```
go에는 class가 없으니 이런식으로 struct를 작성해서 객체화시킨다.
