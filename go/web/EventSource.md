# EventSource
## EventSource 구현 in golang

---
목차
1. [What is EventSource](#EventSource란?)
4. [Field of Application](#활용-분야)

___
## EventSource란?
과거에는 정적인 html만 받아도 됐지만, 동적인 needs가 점점 많아쳐서 

html5기준으로 websocket과 eventSource가 추가되었다.

websocket은 말 그대로 send/receive 문서를 주고받을때 과거에는 request후 response하면 연결이 끊어졌지만, websocket은 계속 연결함으로서 실시간으로 통신이 가능하다.

eventsource는 server가 client에 보내는 연결만 실시간으로 통신이 가능하다.

![image](https://user-images.githubusercontent.com/51067720/122209685-c13d9700-cedf-11eb-9450-b96e5e7f2c1a.png)




___
## 활용 분야

push알림,event 알림 등에 활용 할 수 있다.

