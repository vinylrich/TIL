# JWT란?

session 방식과 jwt방식을 비교해보자.

일단 panorama 프로젝트로 경험해봤던 session/cookie 방식에 대해서 생각해보자.

전체적인 플로우는 이러하다.

1. 사용자 로그인
2. 로그인 시 sessionid를 발급해주고, sessionid를 redis나 expiration을 정할 수 있는 db에 저장해줌.
3. 로그인 됐을 때 클라이언트는 매 요청 헤더에 sessionid를 포함하여 요청함.
4. 서버에서는 sessionid가 db에 저장이 되어 있는지 검증함.


flow에서 볼 수 있듯이 session 방식은 db를 사용해야하며, 이로 인한 추가 비용이 있을 수 있다, 장점이라면 sessionid를 중간에 가로채도 서버 db를 해킹하지 않는 이상 무의미한 값이기 때문에 보안이 좋다는 장점이 있다.

그렇다면 jwt는 무엇일까?

내 식으로 해석해보면 accesstoken은 유저정보라고 보면 된다.

전체적인 플로우는 이러하다.


1. 사용자 로그인
2. 검증 후 서버단에서 accesstoken 발급(만료 정보가 담긴)
3. 클라이언트는 매 요청마다 accesstoken을 헤더에 담아서 줌
4. accesstoken을 secret key로 검증하고 accesstoken이 만료됐으면 재 로그인을 함

jwt를 사용하면 추가적인 db(캐시) 사용이 필요가 없다. 하지만 accesstoken이 즉 유저정보를 주고 받는 것이 때문에 한번 가로채면 유효기간이 지나기 전 까지는 계속 사용할 수 있다.

이에 대한 해결책은 기존의 Access Token의 유효기간을 짧게 하고 Refresh Token이라는 새로운 토큰을 발급하면 Access Token을 탈취당해도 상대적으로 피해를 줄일 수 있다.

물론 Refresh Token도 따로 db를 만들어줘야한다.