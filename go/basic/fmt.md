# Fmt Package

fmt.Println,fmt.Print,fmt.Printf는 알다싶이 콘솔에 출력하는 함수이다.

하지만 fmt.Sprint,f,ln이 있다.
이는 변수에 넣고 사용할 수 있는 함수이다.

예를 들어 "junwoo"라는 문자열을 출력하는 예제가 있다고 하자
```go
case 1:
    fmt.Print("junwoo")
case 2:
    var name string = "junwoo"
    fmt.Print(name)
case 3:
    name:="junwoo"
    nameformat=fmt.Sprintf("%s\n",name)
    
    fmt.Println(nameformat)
```

처럼 출력 할 수 있다는 것이다. 이 이외로도 generic programming처럼 타입을 지정해놓고 변수를 지정해서 여러곳에 사용 할 수 있다.