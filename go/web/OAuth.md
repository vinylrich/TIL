# OAuth

---
목차
1. [What is OAuth](#OAuth란?)
2. [Code](#구현)
3. [Analysis](#코드-분석)
4. [Field of Application](#활용-분야)

___
## OAuth란?
개인정보 관련 법이 많아졌기 때문에 작은회사는 이 법을 다 지키며 db를 관리하는것은 부담이 컸다.

그래서 
자체적인 db를 사용하여 로그인,회원가입을 구현하는 것이 아닌
google이나 facebook같은 기업에서 대신 로그인을 구현해주는 기능이다. 


___
## 구현
google 기준으로 oauth api키를 발급받았다.

1. client가 요청
2. server에서 oath요청
3. oauth 업체에 redirect해줌
4. oauth 업체에서 로그인 process를 끝냄
5. 다시 우리 서버에 callback해줌
6. 사후에 refresh key와 api key를 알려주는데, 이를 통해서 회원정보를 에 접근 할 수 있음.
    - refresh key: 무한정 서버를 열어줄 수 없기 때문에 회원정보에 다시 접근 할 때 필요한 키
    - api key: 회원정보 접근

___
## 코드 분석




___
## 활용 분야

