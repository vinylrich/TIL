# Hash
## Hash 구현 with Golang

내가 짠 코드
Hash.go
```go
type Hash struct {
	Str   string
	H     []int
	Final int
}

func (h *Hash) DoHash(A, B int) {
	for i := 0; i < len(h.Str); i++ {
		if i == 0 {
			h.H[i] = int(h.Str[i]) % B //1번인덱스에
		} else {
			h.H[i] = ((h.H[i-1] * A) + int(h.Str[i])) % B
			if i == len(h.Str)-1 {
				h.Final = h.H[i]
			}
		}
	}
}

```
main.go
```go
func main() {
	h := dataStruct.Hash{}
	A, B := 256, 3571
	h.Str = "abcd"
	h.H = make([]int, len(h.Str)
	h.DoHash(A, B)
	fmt.Println(h.H, "\n", h.Str)
}
```

강좌에서 짠 Hash
hash.go
```go
package dataStruct

//Hi=Hash값(S)
//Str[i]=Si

func DoHash(str string) int {
	h := 0
	A := 256
	B := 3571
	for i := 0; i < len(str); i++ {
		h = ((h * A) + int(str[i])) % B
	}
	return h
}
```

main.go
```go
func main() {
	fmt.Println("abcd = ", dataStruct.DoHash("abcde"))
}
```