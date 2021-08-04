# Singleton Pattern이란?

전역 변수를 사용하지 않고 객체를 하나만 생성 하도록 하며, 생성된 객체를 어디에서든지 참조할 수 있도록 하는 패턴


우리의 application 내에서 언제든지 blockchain의 단 하나의 instance만을 공유하는 방법


변수의 instance를 직접 공유하지 않고, 그 대신 변수의 instance를 우릴 대신해서 드러내주는 function을 생성하는 것.

```go

type block struct {
	data     string
	hash     string
	prevHash string
}

type blockchain struct {
	blocks []block
}

var b *blockchain

func GetBlockchain()*blockchain{
	if b==nil{
		b=&blockchain{}
	}
	return b
}
```

위 코드처럼 GetBlockchain(){}을 선언하면, 우리의 blockchain이 어떻게 초기화되고 공유될지를 제어 할 수 있음