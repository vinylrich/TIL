# slice 사용법

## 기본 문법
<생성><br>
1. slice:=make(data type,len,cap)
<br>
ex)slice:=make([]int,4,8)

2. var slice []int

3. slice:={1,2,3,4,5}

### 다음 배열에 넣는 법

```go
slice:=append(slice,1,2,3,4,5)
```
### slice를 slice하는 방법

slice[:5] 0~4번째 인덱스까지 지정
slice[5:] 5번째부터 끝까지 지정
slice[4:8] 4번째부터 7번째 인덱스까지 지정
