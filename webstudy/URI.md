# URI

## URI URL URN 

### URI

URI는 Uniform Resource Identifier의 약자로 인터넷에 있는 자료의 id이다. identifier니까 겹치면 안됨.

하나의 uri에는 하나의 자원만 참조

### URL,URN

URL은 프로토콜(HTTP,FTP)를 포함한 사이트 도메인을 말한다.
예를 들어 uri가 https://www.naver.com/news?id=123#image 이면,
https://www.naver.com만을 말한다.

URN은 프로토콜을 포함하지 않고 앵커(프레그먼트)앞 까지를 말한다.
uri가 https://www.naver.com/news?id=123#image 이면, www.naver.com/new?id=123 까지를 말한다.

url는 자원의 위치, urn은 자원의 정보를 말할 수 있다.

여기서 새로 나오는 개념이 있다.

바로 anchor(fragment)개념이다.

앵커는 리소스 내에서 딱 그 지점에 위치한 정보를 보여주기 위한 방법이다.

예를 들어 naver.com/new?id=123 이라는 uri가 있으면, 뒤에 #image프레그먼트를 달면 image가 있는 곳으로 바로 스크롤 된다는 의미이다.
