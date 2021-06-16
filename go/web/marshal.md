# Marshal and UnMarshal

## Marshal이란?
논리적 구조를 로우 바이트로 변경하는 것
구조체  v의 JSON 인코딩을 web에 반환하는 데이터를 만드는 것

web의 json 데이터를 구조체 v로 넣는 것-> marshal 혹은 encoding
쉽게 말해서, 구조체 v -> []byte


## UnMarshal
반대로 바이트 슬라이스나 문자열을 논리적 자료 구조로 변경하는 것
JSON 인코딩 데이터를 구문 분석하고 결과를 저장합니다

구조체 v의 데이터를 json 형태로 web에 response 해주는 것-> unmarshal 혹은 decoding

ioutil.ReadAll(resp.Body)//body에 있는 json 포멧을 받아오는 메서드

omitempty란 만약 이 field가 비어있을 경우 json에 표시하지 말라는 뜻이다

[]byte->v

ex)
```go
type dimension struct {
	Height int
	Width int
	}

type Dog struct {
	Breed    string
	WeightKg int
	Size dimension `json:",omitempty"`
}

func main() {
	d := Dog{
		Breed: "pug",
	}
	b, _ := json.Marshal(d)
	fmt.Println(string(b))
}
}
```
결과
```json
{"Breed":"pug","WeightKg":0,"Size":{"Height":0,"Width":0}}
```

```go
func (f *fooHandler) ServeHTTP(w http.ResponseWriter, r *http.Request) {
	user := new(User)
	err := json.NewDecoder(r.Body).Decode(user) //data받아오기
	if err != nil {
		w.WriteHeader(http.StatusBadRequest)
		fmt.Fprint(w, "Bad Request", err)
		return
	}
	user.CreateAt = time.Now()

	data, _ := json.Marshal(user) //
	w.Header().Add("content-type", "application/json")
	w.WriteHeader(http.StatusCreated)
	fmt.Fprint(w,string(data))
```	