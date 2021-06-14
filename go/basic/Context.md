# Context in golang

## 개요
golang에서 뭔가를 만드려면 {ex)웹,앱,임베디드 시스템} 등 꼭 알아야 하는 개념이기 때문에 TIL 적는다. 

## What is Context?
Context 관련 여러가지 post들을 보았지만, 공식 문서 자체에서도 

<b>
Incoming requests to a server should create a Context

서버로 들어오는 요청은 컨텍스트를 생성하고 송신해야 합니다.



이들 사이의 함수 호출 체인은 컨텍스트를 전파해야 하며 선택적으로 WithCancel, WithDeadline,WithTimeout, or WithValue을 사용하여 만든 파생 컨텍스트로 대체해야 합니다.
</b>

와 같이 딱 Context가 무엇인지 한마디로 정의가 되지 않는 것 같다.

내 나름대로 해석해보자면 데이터가 오가는 통로, 유사어를 찾아보면 pipeline정도 되지 않을까 싶다.

_____
## Go 에서의 Context

컨텍스트를 생성하는 방법은 여러가지가 있는데 기본은 context.Background 함수를 사용하여 생성하는 것이다

`func Background() Context`

한번 생성된 컨텍스트는 변경할 수 없다. 그래서 컨텍스트에 값을 추가하고 싶을 때는 context.WithValue 함수로 새로운 컨텍스트를 만들어 주어야 한다.

`func WithValue(parent Context, key, val interface{}) Context`


컨텍스트의 값을 가져올때는 컨텍스트의 Value 메서드를 사용한다.

type Context interface {
	Value(key interface{}) interface{}
}
context.WithCancel 함수로 생성한 컨텍스트에 취소 신호

func WithCancel(parent Context) (ctx Context, cancel CancelFunc)

<br>
<br>
Go Routine을 사용하여 일정 시간이 되면 자동으로 컨텍스트에 취소 신호가 전달되도록 하려면 context.WithDeadline

`func WithDeadline(parent Context, d time.Time) (Context, CancelFunc)`

함수 또는 context.WithTimeout 함수를 사용하여 컨텍스트를 생성하면 된다.

`func WithTimeout(parent Context, timeout time.Duration) (Context, CancelFunc)`

여기까지 종합해봤을 때 Context는 그냥 데이터를 주고받는 통로라고 생각하면 될 것 같다.
_____
## 예제
```go
func main(){
    ctx := context.Background()//make context

    ctx= context.WithValue(ctx,"user",user)// context.WithValue 함수를 사용하여 새로운 컨텍스트를 생성

    UserHandler(ctx)
}
func UserHandler(ctx context.Context) error {
	var user User

    if v := ctx.Value("user"); v != nil {
		u, ok := v.(User)
		if !ok {
			return errors.New("Cause err by not called ctx")
		}
		user = u
	} else {
		return errors.New("Cause err by not called ctx")
	}
}
```


http.Request 패키지에서 Context를 어떻게 사용하는지 살펴보자.

웹 어플리케이션에서 요청이 들어왔을 때 , 요청 작업을 수행 한 후 response를 전달할 때 까지가 하나의 Context라고 볼 수 있다.

request와 response 사이에 유지되어야 할 값이 있다면 그걸 Context에 담아놓고 사용 할 수 있다.


```go

	Method string

	URL *url.URL

	Proto      string // "HTTP/1.0"
	ProtoMajor int    // 1
	ProtoMinor int    // 0

	Header Header

	Body io.ReadCloser

	GetBody func() (io.ReadCloser, error)

	ContentLength int64

	TransferEncoding []string

	Close bool
	Host string


	Form url.Values

	PostForm url.Values

	MultipartForm *multipart.Form

	Trailer Header

	RemoteAddr string

	RequestURI string

	TLS *tls.ConnectionState

	Cancel <-chan struct{}

	Response *Response

	ctx context.Context
}
```

제일 마지막 context가 보일것이다. 이 Context는 request,response process가 완료될 때까지 유지해야 하는 값을 보관한다.

```go
func userHandler(w http.ResponseWriter, r *http.Request){
var user User

    if v := ctx.Value("user"); v != nil {
		u, ok := v.(User)
		if !ok {
			return errors.New("Cause err by not called ctx")
		}
		user = u
	} else {
		return errors.New("Cause err by not called ctx")
	}
}
```
```go
func authMiddleware(next http.HandlerFunc) http.HandlerFunc {
	return func(w http.ResponseWriter, r *http.Request) {
		// 1. 사용자의 현재 세션 정보를 기반으로 currentUser 생성
		user, err := getCurrentUser(r)
		if err != nil {
			http.Error(w, "Not Authorized", http.StatusUnauthorized)
			return
		}

		// 2. 기본 컨텍스트에 current_user를 담아 새로운 컨텍스트 생성
		ctx := context.WithValue(r.Context(), "current_user", user)

		// 3. 새로 생성한 컨텍스트 할당한 새로운 `http.Request` 생성
		nextRequest := r.WithContext(ctx)

		// 4. 다음 핸들러 호출
		next(w, nextRequest)
	}
}
```
사용자의 현재 세션 정보를 기반으로 currentUser를 생성

http.Request의 컨텍스트에 currentUser를 담아 새로운 컨텍스트를 생성
그리고 새로 생성한 컨텍스트 할당한 새로운 http.Request를 생성하여 다음 핸들러를 호출하게 함.