# Stack
## Stack 구현 With Golang

stack.go
```go
type Stack struct {
	ll *LinkedList
}

func NewStack() *Stack {
	return &Stack{ll: &LinkedList{}}
}

func (s *Stack) Empty() bool {
	return s.ll.Empty()
}

func (s *Stack) Push(val int) {
	s.ll.AddNode(val)
}

func (s *Stack) Pop() int {
	back:=s.ll.PopBack()
	return back
}
```
Stack 함수를 선언(define)하는 파일을 하나 만들고, linkedlist 파일에 구현했다.

1. Push 메서드는 LinkedList의 AddNode 메서드와 상당히 유사하나, Push 메서드는 Tail을 출력해야하기 때문에 따로 만들었다.
2. Empty 메서드는 stack이 비어있는지 확인하기 위한 메서드이다.

```go
func (l *LinkedList) PopBack() int{
	if l.Tail != nil {
		val=l.Tail.Val
        l.RemoveNode(l.Tail)
        return val
	}else{
        return 0
    }
}
```

1,2,3,4,5,6 순으로 Push 했다고 가정해보자. Popback이 실행되며 Tail을 remove하고, back은 변수에 넣고 return 하여 print하기 위하여 만들었다.
RemoveNode에서는 Tail을 Tail.Prev로 바꾸는 작업을 할 것이다.

좀 더 기능적인 방식으로 리펙토링한 코드이다.
```go
func (l *LinkedList) Back() int {
	if l.Tail != nil {
		return l.Tail.Val
	}
	return 0
}
func (l *LinkedList) PopBack() {
	if l.Tail == nil {
		return
	}
	l.RemoveNode(l.Tail)
}
```