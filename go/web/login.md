# login in golang

OAUTH에서 사용자가 login을 하면 
session ID를 발급해준 후, 인메모리상에 사용자의 profile이 오면 백엔드에서 바로 사용할 수 있지만 
browser에서 페이지를 바꿔도 유지해야하기 때문에 local storage에 넣어줘서cookie로 저장해야한다.

cookie에 pwd를 넣으면
스누핑을 통해 패킷을 읽어볼 수 있음.
그래서 쿠키를 못 까게 해야함

그래서 암호화를 함
http->https
평문 프로토콜을 중간에 깔 수 없게
암호화를 함