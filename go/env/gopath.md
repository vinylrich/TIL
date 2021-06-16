# GoPath

## Gopath란?
초기 golang이 발표될 때 go 프로그램은 무조건 gopath/src에 있는 코드만 돌아가게 설계되었다.

대부분의 초기 gopath는 c:/user/유저이름/go

하지만 자신의 프로젝트에 이 gopath 이외로 사용할 곳에 성격이 맞지 않는다던가

내부 패키지 뿐만 아니라 외부 패키지를 만들어 사용하는 도중 이미 go get을 하여 설치한 외부 패키지와 업데이트가 된 같은 외부 패키지를 go get 할 때 버전 충돌의 문제가 생긴다.

ex) gorilla/mux 1.2 버전을 깔고,uuid 0.8버전을 깔았는데 uuid 버전이 1.3으로 업데이트 되어서 mux와 호환이 안되는 상황이 생길 수 있었다.

프로젝트 version을 고정 시키고 싶은데

gopath/pkg
하나의 pkg가 update 되면 다른 pkg들도 update된다.



## 그래서 생겨난 GoModule

1.5버전이 최종 버전임에도 나는 1.2버전을 쓰고싶은데 자동 update 되니까 불편했다
->vender 생겨남.

또 이에 대한 요구 사항들이 많아지다 보니까 Go 1.12버전에 GoModule이 생겨났다.

heroku로 배포하기 위해서는 gomodule을 사용해야한다.

GoMoudle이 뭐냐?

GOPATH 이외의 작업 폴더에서 GO 프로그램을 개발 할 때, 
import를 하거나 go get을 하면 go.mod 파일에 자동으로 import되는 기능이다.   