# Tree DFS (Tree와 이어짐)

## DFS란?
### 깊이 우선 탐색,Depth First Search의 약자이다

말 그대로 깊은 곳부터 탐색하는 탐색기법이다.

![img](https://user-images.githubusercontent.com/51067720/119223355-e8e54d80-bb33-11eb-8f78-cdbf264f173a.gif)
출처: https://developer-mac.tistory.com/64

위 gif와 같은 프로세스로 진행된다.

DFS는 두 가지로 구현 할 수 있다.
1. 재귀호출
2. 스택

본격적으로 코드를 보도록 하겠다.
```GO
func (t *Tree) DFS1() {
	DFS1(t.Root)
}
func DFS1(Node *TreeNode) {
	fmt.Printf("%d->", Node.Val)

	for i := 0; i < len(Node.Childs); i++ {
		DFS1(Node.Childs[i])
	}
}

func (t *Tree) DFS2() {
	s := []*TreeNode{}
	s = append(s, t.Root)

	for len(s) > 0 {
		var last *TreeNode
		last, s = s[len(s)-1], s[0:len(s)-1] 
		fmt.Printf("%d->", last.Val)

		for i := len(last.Childs) - 1; i >= 0; i-- {
			s = append(s, last.Childs[i])
		}
	}
}
```

DFS1이 재귀호출,DFS2가 스택으로 구현한 DFS이다.

재귀호출은 복습이 끝난 후 나중에 해석해보도록 하고 스택으로 구현한 DFS 코드를 해석하도록 하겠다.

![화면 캡처 2021-05-22 191720](https://user-images.githubusercontent.com/51067720/119223087-67d98680-bb32-11eb-8c56-0ce5c6fd3a21.png)
트리 구조가 위와 같다고 가정해보자.
위 GIF DFS 하려면 1,2,5,6,3,7,8,4,9,10의 순서대로 탐색되어야한다.

Stack으로 구현하기 위해 TreeNode타입의 stack을 선언한다.
Stack을 구현하기 위한 주요 코드인

```go
last, s = s[len(s)-1], s[0:len(s)-1]
```
제일 뒤에 노드는 Pop하고, 기존 스택을 제일 뒷 노드를 제외한 스택을 재선언한다.
1. 처음 for문에 진입했을 때 Root가 진입이 된다. 
2. Root는 1이기 때문에 1이 출력된다.
3. 안에 있는 for문에 진입하면, 1의 자식의 개수에 따라 for문이 시작되며,
4. 끝 노드부터 4,3,2가 stack에 삽입된다.
5. 다시 포문을 돌아 2가 출력되고, 이중포문으로 들어가 2의 자식 개수에 따라 6,5가 stack에 삽입된다.
6. 끝 노드부터 5가 출력이 된다.


종합적으로 Print하면 1,2,5,6,3,7,8,4,9,10의 순으로 Print된다.
