# MSA란 무엇인가?
### 정의:Micro Service Architecture의 약자로, 하나의 기능을 하나의 프로젝트로 만드는 아키텍쳐
### 모든 기술을 하나의 프로젝트에 구현하는 Monolithic Architecture와는 상반되는 개념이다.

#### 등장 배경: 서비스/프로젝트가 커지면 커질수록 영향도 파악 및 전체 시스템 구조 파악의 어려움이 있었음.

각각의 기능에 장애 처리가 가능하게끔 한 아키텍쳐
네이버를 본다고 생각하면
각각 부분들을 따로따로 서비스를 만드는 아키텍쳐
a서비스와 b 서비스가 바뀌어도 상관없이 계속 서비스만 만들고 가져와서 쓰는것

serverless
기존

사용자<->웹서버

여러 서버들로 작게작게 나누어서 여러 서버들을 적게적게 사용하는 것

ECS(Entity Component System)

Entity가 가르키는 방향에 따라 Entity가 뭔지 달라짐
Component가 data를 가지고 있고
system이 기능을 가지고 있음

MVC

MODEL-VIEW-CONTROLLER

서로간의 종속성을 끊자! 분리하자!