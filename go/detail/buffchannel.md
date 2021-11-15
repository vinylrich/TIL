# buffered channel unbuffered channel

기본적으로 모든 채널은 unbuffered이다

unbuffered란? 

하나의 메세지를 받으면 blocking 함

c := make(chan int,5)

사이즈를 정해주면 buffered 채널이 된다.