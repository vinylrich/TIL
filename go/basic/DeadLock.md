# DeadLock
## DeadLock in golang

---
목차
1. [What is DeadLock](#DeadLock이란?)
2. [Code](#구현)
3. [Analysis](#코드-분석)
4. [Field of Application](#활용-분야)

______
## DeadLock이란?

둘 이상의 작업이 서로 상대방의 작업이 끝나기만을 기다리고 있는 상황이다.

간헐적으로 발생
lock을 작게잡거나(지역) 크게잡기(광역)


실제 실무에서는 굉장히 복잡하게 문제가 생김.
데드락 상황이 발생하면 굉장히 풀기 어려움

여러명이 같은 자원을 헝클어놓기 때문에 발생하는 문제

컨베이어벨트방식(분업)
각자 맡은 바 일만 함
producer-consumer pattern

->channel
Thread safe
fixed size
성능이 뛰어난 queue

```go
package main

import "fmt"

func pop(c chan int) {
	fmt.Println("pop") //3
	v := <-c           //4
	fmt.Println(v)     //5
}
func main() {
	c := make(chan int) //1

	go pop(c) //2
	c <- 10   //5

	fmt.Println("end of program") //5,6
}

/*goThread 1
Main함수
goThread생성
pop 실행
*/

/*process
Main thread 실행
pop thread 실행
pop thread에서 v에 c값이 들어갈때까지 기다림
c에 10이 들어감
v출력

이걸 통해서 컨베이어시스템
producer-consumer시스템을 만들 수 있음
자신이 1을 다 하면 2를 하기 위해 다른사람에게 넘김
2를 다 하면 3을 함 넘기는 과정에서 channel사용
*/

```
why multiThread?
-머신의 효율을 최대한
-공짜 점심이 끝났다.
-무어의 법칙
이 깨졌기 때문 1년마다 cpu가 두배 더 좋아지게 만들겠다
-너무 작게 만들다 보니까 물리적 한계 열,전자방해,자기방해
인텔- 멀티코어로
가만히 있어도 프로그램이 두배씩 빨라짐-공짜점심
지금은 그러지 않음

멀티쓰레드를 사용하지 않아도 됨
멀티프로세스
1개 프로세스가 4개 쓰레드=4개 프로세스가 1개 쓰레드

가상화를 이용해서 싱글스레드를 갖는 경우도 있음

멀티 프로세스로 가는 상황도 있고 멀티 쓰레드로 가는 상황도 있음
