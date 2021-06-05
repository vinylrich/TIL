```go
	w.Header().Add("Content-type", "application/json")
	w.WriteHeader(http.StatusOK)
	data, err := json.Marshal(user)
	if err != nil {
		w.WriteHeader(http.StatusBadRequest)
		fmt.Fprint(w, err)
		return
	}
```
와 같은 반복되는 코드를 간소화 시키기 위해
unrolled/render 패키지를 다운받는다.    