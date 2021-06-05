# Tree BFS (Tree와 이어짐)

## Tree BFS 구현 in Golang
---
목차
1. [What is tree BFS?](#BFS란?)
2. [Code](#구현)
3. [Analysis](#코드-분석)
4. [Field of Application](#활용-분야) 
_____
## BFS란?
### 너비 우선 탐색,Breadth First Search의 약자이다

넓이를 기준으로 탐색한다는 의미이다.
![다운로드](https://user-images.githubusercontent.com/51067720/119223768-277c0780-bb36-11eb-8cee-6dc12c1ea15c.gif)
출처: https://developer-mac.tistory.com/64

위 gif와 같은 프로세스로 진행된다.
_____
## 구현
BFS는 queue로 구현할 수 있다.

본격적으로 코드를 분석해보도록 하겠다.
```go
func (t *Tree) BFS() {
	queue := []*TreeNode{}
	queue = append(queue, t.Root)

	for len(queue) > 0 {
		var first *TreeNode
		first, queue = queue[0], queue[1:]
		fmt.Printf("%d->", first.Val) //찾기
		for i := 0; i < len(first.Childs); i++ {
			queue = append(queue, first.Childs[i])
		}
	}
}
```
______
## 코드 분석
![화면 캡처 2021-05-22 191720](https://user-images.githubusercontent.com/51067720/119223087-67d98680-bb32-11eb-8c56-0ce5c6fd3a21.png)
트리 구조가 위와 같다고 가정해보자.
위 GIF처럼 BFS하려면 1,2,3,4,5,6,7,8,9,10 순으로 출력되어야 한다.

아래 코드는 queue를 구현하기 위한 아주 중요한 코드이다
```go
first, queue = queue[0], queue[1:]
```
처음 node는 pop하고, 그 다음 queue에 pop한 노드를 없애고 제선언한 코드이다.

1. queue를 선언 후 처음엔 Root treenode로 접근된다.
2. Root는 1이기 때문에 1이 출력되고, 안의 for문에서는 1의 childs인 순서대로 2,3,4순으로 queue에 저장된다.
3. 다시 첫 for문으로 돌아가 2가 pop되고, 2의 자식인 5,6이 queue에 들어간다
4. 그럼 현제 queue에는 3,4,5,6이 남는다


종합적으로 1,2,3,4,5,6,7,8,9,10가 출력된다.
_____
## 활용 분야
활용분야:미로 찾기 등 최단거리를 구해야 할 경우