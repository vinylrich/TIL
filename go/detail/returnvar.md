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