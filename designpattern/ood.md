# OOD


object oriented design

object 중심의 설계

수백명의 프로그래머가 하나의 프로그램을 만듦
모든 일을 조율해주고 전체 구조를 짜야 함:아키텍쳐

설계를 잘 해야함
OOD

1. [S](#S-Single-Responsibility-Principle)
2. [O](#O-Open-Closed-Principle)
3. [L](#L-Liskov-subtitution-Principle)
4. [I](#I-Interface-segregation-principle)
5. [D](#D-Dependency-inversion-principle)
6. [problem of oop](problem-of-oop)

모든 원칙은 무조건 최고가 아니라, 이렇게 가는게 좋다 라는 마음가짐
## S-Single Responsibility Principle
단일 책임 원칙
ex)예금잔고 객체가 있음
입금 출금 따로 만드는게 좋을지, 입출금 함수를 같이 만드는게 좋을지


______
## O-Open Closed Principle
확장에는 열려있고 변경에는 닫혀있다.

기존에 만든 것을 건들이지 않고 새로운 기능만 추가해주면 되므로 유지보수가 편함

## L-Liskov subtitution Principle

o(x) x는T
o(y) ysms S<-T

Base Type의 기존 함수를 바꾸지 말라

extended type이 parent를 바꾸지 말라

golang은 상속이 없다!!!!
걱정 ㄴㄴ


## I-Interface segregation principle

여러개의 관계를 모아놓은 인터페이스보다
관계 하나씩 정의하는게 더 좋다
인터페이스에 다 넣지 말라!
## D-Dependency inversion principle
관계는 인터페이스에 의존해는게 객체에 의존하는 것 보다 더 좋다


항상 염두해두면 더 나은 프로그래머가 될 수 있음
지향해야될 목표

검토,개선

## problem
oop가 성공하고 난 후, 모든 개발자에게 oop는 필수가 되었다

oop는 잘하기 어렵다!!ㅠㅠ
지식만 가지고는 oop를 잘 할 수 없다. 올바르게 숙달시켜야함

oop로 짠다는 건 object가 엄청나게 많아짐
새로운 프로그래머가 들어오면 기존에 잘 짜여진 프로그램을 숙달하는 시간이 오래걸림

1. 잘 만들기 어렵고
2. 잘 만들어진 프로그램을 새로운 프로그래머가 파악하는데 시간을 너무 오래걸림.


실리콘밸리
make fast
break things
제품을 빨리 만들어야함
-> 설계원칙 x
성공했을 경우.. 
기반이 잡혀있지 않으면 견딜수가 없음


Make fast
Low Tech dept

절차적->oop->stateless

왜 변경사항이 많을 때 어려운가?
상태와 기능이 분리되어 있어서

상태와 기능이 엇갈림(혼재됨)

프로그래밍->레고방식으로 바뀜

프로그래머들이 자기가 맡은 분야만(모듈만) 만들어서 조립할 수 있게 함
상태를 없애버리고 기능만 만들자
상태는 외부에서 가져오기

- micro Server
- serverless 
- Functional language
- 게임:ecs
- 웹:mvc

 서로 분야는 다르지만 근본적인 기능들을 분리하여 하나의 서비스로 제공한다는 것은 바뀌지 않는다.


 Functional language
 기능o 상태x
 순수하게 기능만 가져가자