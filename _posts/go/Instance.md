# golang에서의 Instance


golang에서는 class 개념이 없기 때문에 struct와 Interface를 활용하여 객체화시킬 수 있다.

가장 대표적인 예로

```go
type Student struct {
	name  string
	age   int
	grade int
}

//Reference type
func (t *Student) SetName(newName string) {
	t.name = newName
}
func main() {
	a := Student{"junwoo", 20, 3}
	a.SetName("bbb")
	fmt.Println(a)
}
```

위 코드를 해석해보자면 Student라는 변수를 만들고, Student 자체의 기능(메소드)인 SetName을 변수명 a.SetName과 같은 형태로 사용하는 코드이다.

## golang에서 struct?
golang에서 struct는 
property와 method 둘 다 가질 수 있다.
golang의 언어를 개발하는 사람들이 현대 개발은 OOP를 지향하고있는 추세이기 때문에 CLASS를 없애는 대신 이러한 기능을 넣은 것 같다.

struct의 기능을 사용하려면 위의 코드와 같이 사용하면 되지만, 

```go

//Reference type
func (t *Student) SetName(newName string) {
	t.name = newName
}
func SetName(t Stduent,newName string)
func main() {
	a := Student{"junwoo", 20, 3}
    
	a.SetName("bbb")
    SetName(a,"bbb")
	fmt.Println(a)
}
```

위 코드를 보면 두 가지의 SetName이 있다.
일단 결론부터 말하지면 컴퓨터 상에서의 둘의 차이는 **없다**

하지만, 개발자가 개발을 하면서의 차이는 아주 크다

우선 첫 번째 a.SetName은 객체 단위의 시각으로 보는 것이고
두 번째 SetName은 기능 단위로 보는 것이다.

OOP로 프로그래밍하려면 첫 번째 객체 단위의 시각으로 코딩하는 것이 맞다. 