# Queue
## Queue 구현 in Golang

---
---
목차
1. [What is tree Queue?](#Queue란?)
2. [Code](#구현-및-분석)
3. [Field of Application](#활용-분야) 
____

## Queue란?
줄, 줄을 서서 기다리는 것을 의미하며 선입선출(먼저 들어온 자원은 먼저 나간다)의 특징을 가지고 있다.
![다운로드 (1)](https://user-images.githubusercontent.com/51067720/119442260-73ab8f80-bd62-11eb-9b26-a0f0fb555bdc.png)
사진 출처:https://devuna.tistory.com/22

____
## 구현 및 분석
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

____
## 활용분야

- 우선순위가 같은 작업 예약 (프린터의 인쇄 대기열)
- 은행 업무
- 콜센터 고객 대기시간
- 프로세스 관리
- 너비 우선 탐색(BFS, Breadth-First Search) 구현
- 캐시(Cache) 구현
