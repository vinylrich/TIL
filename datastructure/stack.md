# Stack
## Stack 구현 in Golang

----
목차
1. [What is tree Stack?](#Stack이란?)
2. [Code](#구현-및-분석)
3. [Field of Application](#활용-분야) 
____

## Stack이란?
Stack이란 쌓아올리다라는 의미를 가지고 있다.
말 그대로 쌓아올리는 자료구조이다.
Stack은 후입선출이라는 특징을 가지고 있다.
![다운로드](https://user-images.githubusercontent.com/51067720/119442102-2fb88a80-bd62-11eb-8bb4-02b5105399bb.png)
사진 출처:https://devuna.tistory.com/22

___
## 구현 및 분석

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
____
## 활용 분야
stack의 활용 분야는
- 웹 브라우저 방문기록 (뒤로 가기) : 가장 나중에 열린 페이지부터 다시 보여준다.
- 역순 문자열 만들기 : 가장 나중에 입력된 문자부터 출력한다.
- 실행 취소 (undo) : 가장 나중에 실행된 것부터 실행을 취소한다.
- 후위 표기법 계산
- 수식의 괄호 검사 (연산자 우선순위 표현을 위한 괄호 검사)