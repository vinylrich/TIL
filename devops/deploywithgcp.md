# gcp GCE로 배포하는 방법

1. v1

일단 VM 인스턴스를 만들고 SSH 터미널에 접속한다.

접속 한 뒤

` git clone github.com/Username/Projectname ` 을 입력하고 appilcation을 다운로드받는다.

` go mod tidy `로 의존성을 다운 받은 후

` go build ` 로 빌드를 하며 서버 실행파일을 만든다.

` nohup ./ProjectName ` nohub명령어로 서버 vm인스턴스가 꺼지지 않고 백그라운드에서 실행 시킬 수 있다.

기본적으로 터미널에서 세션 로그아웃을 하면

리눅스는 해당 터미널에서 실행한 프로세스들에게 HUP signal 이 전달하여 종료시키게 되는데,

이 HUP signal을 프로세스가 무시(ignore)하도록 하는 명령어라서 nohup 이라는 이름인 것이다.

nohup.out 파일을 생성하지 않으려면 표준 출력과 표준 에러를 /dev/null 를 사용하면 됨.

`nohup [프로세스] 1>/dev/null 2>&1 &`

 
nohup 후 ssh 접속을 끊었다가 다시 프로세스가 돌아가는것을 확인하려면
`ps -e` 명령어를 실행하면 된다.