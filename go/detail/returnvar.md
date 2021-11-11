# return var

```go
func restoreKey() (key *ecdsa.PrivateKey) {
	walletbytes, err := os.ReadFile(walletFilename)
	utils.HandleError(err)

	key, err := x509.ParseECPrivateKey(walletbytes)
	utils.HandleError(err)
    return
}
```

return 할 var이름을 명시해주면 key를 이미 알고 있기 때문에 굳이 return 해주지 않아도 key를 return 한다

function을 축약해서 볼 때 return var를 함수를 펼치지 않고 볼 수 있기 때문에 장점이 있다.

이 기능은 very short function에만 사용해야 한다