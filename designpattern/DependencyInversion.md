# Dependency Inversion 이란?

Dependency Inversion은 하이 레벨의 로직이 로우레벨의 로직에 의존해서는 안된다는 원칙이다.

https://play.golang.org/p/2RLJmOT1-sI

https://play.golang.org/p/uNO0zNvrG4f

이 원칙을 잘 해결한 예시다.

위의 링크에 있는 코드는 주석을 달아서 postgre를 쓸 땐 postgre만, mysql을 쓸 땐 mysql만 사용하도록 할 수 있다.

이렇게 되면 코드의 유동성이 떨어진다.

GetUsers 함수를 선언 후 DBConn이 mysql, postgresql 모두 query라는 함수가 있기 때문에 둘 다 선언하는 것을 만족한다.

코딩이라는것.. 생각보다 쉽지 않구나

참고: https://jusths.tistory.com/210