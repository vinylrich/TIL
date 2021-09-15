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

ONDO 에서는 google과 kakao oauth 2.0을 사용할 예정이다.

google 기준의 기본적인 oauth flow는 

1. client에서 google 로그인을 요청한다.
2. google 페이지에서 로그인 or 회원가입을 요청 한다.
3. google에서 로그인 process를 끝내고 서버의 리다이렉션 url에 https://test.com/auth/google/callback?code=코드 의 형태로 코드를 보내준다.
4. https://www.googleapis.com/oauth2/token
POST Body 정보: code=코드정보, client_id=클라이언트-아이디, client_secret=클라이언트-비밀번호, redirect_uri=https://www.test.com/auth/google/callback 와 같이 코드정보와 클라이언트 아이디 비밀번호를 googleapis에 POST로 요청하면 accesstoken을 리다이렉션 url로 전송해준다 
```json
    {
        "access_token" : "ya29.AHES6ZTtm7SuokEB-RGtbBty9IIlNiP9-eNMMQKtXdMP3sfjL1Fc",
        "token_type" : "Bearer",
        "expires_in" : 3600,
        "refresh_token" : "1/HKSmLFXzqP0leUihZp2xUt3-5wkU7Gmu2Os_eBnzw74"
    }
```
5. 이 access_token을 사용해서 유저의 구글 계정 프로필 정보를 가져올 수 있다. 예를 들어, https://www.googleapis.com/oauth2/v3/userinfo 라는 URL에 우리의 액세스 토큰 정보를 포함하여 GET 요청을 보내면
6. 
```json
    {
        "sub": "110248495921238986420",
        "name": "Aaron Parecki",
        "given_name": "Aaron",
        "family_name": "Parecki",
        "picture": "https://lh4.googleusercontent.com/  -kw-iMgD
   _j34/AAAAAAAAAAI/AAAAAAAAAAc/P1YY91tzesU/photo.jpg",
        "email": "aaron.parecki@okta.com",
        "email_verified": true,
        "locale": "en",
        "hd": "okta.com"
    }
```

와 같이 유저 정보를 넘겨 받을 수 있다.
7. 이런 엑세스 토큰과 리프레시 토큰은 브라우저의 캐시로 저장하거나 redis같은 세션 캐시에 저장할 수 있다.
___

