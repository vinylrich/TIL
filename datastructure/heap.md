# Heap
## Heap 구현 in Golang
_____
1. [What is Heap](#Heap란?)
2. [Code](#구현-및-분석)
3. [Field of Application](#활용-분야)

___
## Heap이란?
Heap은 우선순위 큐(Priority Queue)를 위해서 만들어졌다.

heap은 maximum heap과 minimum heap으로 나누어진다.

![image](https://user-images.githubusercontent.com/51067720/120474302-01325380-c3e3-11eb-8098-37fff1c8a08f.png)
사진출처: https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html

maximum heap은 부모 노드의 key값이 자식 노드의 key값보다 크거나 같은 완전 이진 트리
minimum heap은 부모 노드의 key값이 자식 노드의 key값보다 작거나 같은 완전 이진트리이다.

자식의 순서는 왼쪽 오른쪽 상관이 없다!

___
## 구현 및 분석
힙을 저장하는 표준적인 자료구조는 배열이다.
구현을 쉽게 하기 위하여 배열의 첫 번째 인덱스인 0번인덱스는 

힙에서의 부모 노드와 자식 노드의 관계
왼쪽 자식의 인덱스 = (부모의 인덱스) * 2
오른쪽 자식의 인덱스 = (부모의 인덱스) * 2 + 1
부모의 인덱스 = (자식의 인덱스) / 2(integer)


___
## 활용 분야

왜 Priority Queue를 만들기 용이한가!
최대값,최솟값을 찾는데 용이하기 때문 

이 Priority Queue는
- 시뮬레이션 시스템
- 네트워크 트래픽 제어
- 운영 체제에서의 작업 스케쥴링
- 수치 해석적인 계산

등으로 활용 할 수 있다.!
