# Tree
## Tree 구현 in Golang
---
목차
1. [What is tree Tree?](#Tree란?)
2. [Code](#구현)
3. [Analysis](#코드-분석)
4. [Field of Application](#활용-분야) 
_____
## Tree란?
tree는 **노드로 이루어진 자료구조**로 
1. 하나의 루트 노드를 가지고 있음
2. 루트 노드는 0개 이상의 자식 노드를 갖고 있다.
3. 그 자식 노드 또한 0개 이상의 자식 노드를 갖고 있고, 이는 반복적으로 정의됨
___
## 구현
### 노드 구조

```go
type TreeNode struct {
	Val    int
	Childs []*TreeNode
}
type Tree struct {
	Root *TreeNode
}
```
자식노드와 값을 struct로 선언한다.
Root로 사용할 TreeNode를 한 번 더 선언함으로써 Root에서 Child를 접근 할 수 있도록 한다.

```go
func (t *TreeNode) AddNode(val int) {
	t.Childs = append(t.Childs, &TreeNode{Val: val})
}
func (t *Tree) AddNode(val int) {
	if t.Root == nil {
		t.Root = &TreeNode{Val: val}
	} else {
		t.Root.Childs = append(t.Root.Childs, &TreeNode{Val: val})
	}
}
```

main.go
```go
tree := dataStruct.Tree{}
	val := 1

	tree.AddNode(val)
	val++

	for i := 0; i < 3; i++ {
		tree.Root.AddNode(val)
		val++
	}
	for i := 0; i < len(tree.Root.Childs); i++ {
		for j := 0; j < 2; j++ {
			tree.Root.Childs[i].AddNode(val)
			val++
		}
	}
```
____
## 코드-분석
위 코드를 해석하면 
1을 Root로 넣고,
1. 첫 번째 for문에서는 1의 기능의 AddNode를 해서 1의 자식에 2,3,4를 넣는다
2. 두 번째 for문에서는 차례대로 2의 자식에 5,6을 넣고
3의 자식에 7,8을 넣고
4의 자식에 9,10을 넣는 구조이다


___
## 활용 분야
디렉터리 구조,조직도

main함수에서 Tree를 다음과 같이 넣었다고 가정하자.
![화면 캡처 2021-05-22 191720](https://user-images.githubusercontent.com/51067720/119223087-67d98680-bb32-11eb-8c56-0ce5c6fd3a21.png)
트리 구조는 위 그림과 같을 것이다.

tree BFS와 DFS에서 계속.