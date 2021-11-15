# How to seperate Receive Channel and Send Channel

```go
//보내기 전용 채널
func countToTen(c chan<- int) {
	for i := range [10]int{} {
		fmt.Println(i, c)
		c <- i
		time.Sleep(1 * time.Second)
	}
	close(c)
}

func receive(c <-chan int) { //받기 전용 채널
	for {
		a, ok := <-c

		if !ok {
			fmt.Println("NO VALUE")
			break
		}
		fmt.Println(a)

	}

}

```

보기와 같이 변수값과 chan 사이에 <-이 있으면 받기 전용 채널이고, chan과 type 사이에 <-이 있으면 보내기 전용 채널이다.