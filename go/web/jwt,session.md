# JWT, Session 인증 방식

## JWT 인증 방식

JWT 인증 방식의 프로세스는 

CLIENT LOGIN -> 서버에서 사용자가 맞는지 판단-> 맞으면 ACCESS TOKEN을 RESPONSE해주고, 이를 CLIENT 브라우저의 로컬스토리지에 저장한다. 그리고 client에서는 요청 시 저장된 TOKEN을 매 REQUEST마다 헤더에 넣어 server에서 이를 검증한다.
____
## Session 인증 방식
SESSION 인증 방식의 프로세스는  
CLIENT LOGIN-> 서버에서 사용자가 맞는지 판단-> 세션을 식별하기 위한 SESSION ID를 기준으로 정보 저장
브라우저에 쿠키로 SESSION ID 저장

해당 사이트에 대한 모든 REQUEST에 SESSION ID를 쿠키에 담아 전송
____
    
## 정리
정리해보자면, 
세션 방식은 쿠키에 저장되어 매 HTTP요청마다 포함되어 로그인 구현에 용이하다.

jwt방식은 로컬 스토리지에 저장되어 클라이언트에 대해서 모든 요청에 대해 로컬 스토리지에 있는 token을 사용한다.

둘의 가장 큰 차이점은 세션기반은 서버에 유저의 정보를 저장하고, jwt는 안한다는 것이다.