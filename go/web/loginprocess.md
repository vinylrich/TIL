# login 과정
## login-process

1. 사용자가 아이디와 비밀번호 입력하여 로그인 시도
2. 사용자가 입력한 비밀번호는 암호화되어 DB에 저장된 비밀번호화 같은지 판별
3. 판별 결과가 참이면 Client에 access token 전송
4. 로그인 성공 후 access token을 request에 넣어서 서버에 전송하면 로그인 유지 및 서비스 사용
____
## athentication과 authorization(허가)

## athentication(인증)
athentication이란 login-process에서 2,3번에 해당하는 행위이다.

한 마디로 표현하자면 이 아이디와 비밀번호가 우리 db에 있냐 없냐 판별하는 과정이다.

즉, 라우터에서 컨트롤러가 호출되고, 컨트롤러 내 인증 미들웨어에서 DB에 저장된 비밀번호화 같은지 판별하는 과정과, 판별 결과가 참이면 client에 access token을 전송하는 과정을 authentication이라고 한다.

이 access token을 생성 할 때 자주 사용되는 것이 JWT(JSON WEB TOKEN)이다.

JWT는 CLIENT와 SERVER간에 유저 정보를 담은 JSON 데이터를 암호화 후 주고 받는 방법이다.


___
## authorization(허가)
authorization이란 한마디로 표현하자면 권한을 부여하는 것을 말한다.

ex)게시판 글 쓰기

login-process의 3,4번 process를 보면, 판별 결과가 참이면 client에 access token을 전송한다는 과정을 알 수 있다. 
 
허가도 JWT를 통해 구현될 수 있다.

access token으로 유저 정보를 얻을 수 있고, 어떤 권한이 있는지 판별 할 수 있다.

user id를 사용해서 데이터베이스에 해당 유저의 권한(permission)을 확인합니다.

서버에서 해당 유저 정보를 통해 권한(permission)을 확인하여 해당 요청 처리

유저가 권한을 가지고 있지 않으면 Unauthorized Response(401) 혹은 다른 에러 코드를 보냅니다.