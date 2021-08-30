# CORS error

드디어 말로만 듣던 CORS 에러에 직면했다.

## What is CORS Error???

CORS는 (Cross-Origin Resource Sharing)의 약자로 추가 HTTP HEADER를 사용해서, 한 DOMAIN에서 실행중인 웹 애플리케이션이 다른 DOMAIN의 선택한 자원에 접근 할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제이다.

웹 애플리케이션은 리소스가 자신의 도메인,프로토콜 포트와 다를 때 CORS HTTP 요청을 실행한다.

EX) 30.45.65.223에 API SERVER를 띄웠는데, 20.46.43.220에서 30.45.65.223 작업을 요청하려고 할 때 추가 HTTP HEADER를 사용해서 다른 DOMAIN에서 접근 할 수 있는 권한을 부여해야한다.


그 해더는 바로바로

`ACCESS-CONTROL-ALLOW-ORIGIN`이다

golang gin-gonic에서는 CORSMiddleware를 통해서 해결 할 수 있다.

