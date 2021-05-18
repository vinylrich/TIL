# 11.9 JWT
## GCS 개발

LOGIN을 POST로 요청하고, 응답 받았을 때

JSON FORMAT의 TOKEN을 브라우저의 LocalStorage에 저장

프론트엔드는 그걸 이용해서 새로고침해도 로그인이 풀리지 않도록 함(쿠키역할)
로그인 판별