# Queue
## Queue 구현 With Golang

queue.go
```go
type Queue struct {
	ll *LinkedList
}

func NewQueue() *Queue {
	return &Queue{ll: &LinkedList{}}
}

func (q *Queue) Push(val int) {
	q.ll.AddNode(val)
}

func (q *Queue) Pop() int {
	front := q.ll.Front()
	q.ll.PopFront()
	return front
}

func (q *Queue) Empty() bool {
	return q.ll.Empty()
}
```

1. Push 메서드는 LinkedList의 AddNode 메서드와 상당히 유사하나, Push 메서드는 Tail을 출력해야하기 때문에 따로 만들었다.
2. Empty 메서드는 queue가 비어있는지 확인하기 위한 메서드이다.


```go

func (l *LinkedList) Front() int {
	if l.Root != nil {
		return l.Root.Val
	}
	return 0
}

func (l *LinkedList) PopFront() {
	if l.Root == nil {
		return
	}
	l.RemoveNode(l.Root)
}
```

code를 분석해보면 stack은 Tail을 remove했던 것에 비교하여 queue는 Root를 먼저 없애는 걸 알 수 있다.
RemoveNode는 Root를 없애고 Root.Next를 Root로 만드는 작업을 한다.
