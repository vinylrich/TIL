```go
http.Handle //구조체를 받아서 구조체 내의 기능으로서 사용하는 handler 사용하려면 ServeHTTP함수를 사용해야함.
http.HandleFunc


http.ResponseWriter.Header.Add("Contents-Type","application/json")
err := json.NewDecoder(r.Body).Decode(user)//user에 POST방식으로 값을 받은 json 형식을 Decode 해주는 함수이다.

http.ResponseWriter.WriteHeader(http.StatusOK)
rd.JSON(w, http.StatusOK, user)//로 위 두 문장 대체
1.
`
    http.Handle("/", http.FileServer(http.Dir("public")))
	http.HandleFunc("/upload", uploadHandler)
	http.ListenAndServe(":3002", nil) 
`
2.
`	
    mux := mux.NewRouter()
	mux.HandleFunc("/", indexHandler)
	mux.HandleFunc("/users", usersHandler).Methods("GET") //users가 없으면 상위 핸들러가 호출됨
	mux.HandleFunc("/users", createUserHandler).Methods("POST")
	mux.HandleFunc("/users", updateUserHandler).Methods("PUT")
	mux.HandleFunc("/users/{id:[0-9]+}", getUsersInfoHandler).Methods("GET")

	// mux.HandleFunc("/users", deleteUserHandler).Methods("DELETE")
	return mux  
`
3.
`
    rd = render.New()

    mux := pat.New()
    mux.Get("/users", getUserInfoHandler)
    mux.Post("/users", addUserHandler)
    mux.Get("/hello", helloHandler)

    n := negroni.Classic()//미들웨어 negroni
    n.UseHandler(mux)
    http.ListenAndServe(":3000", n)
`
data, _ := json.Marshal(updateUser)
// 구조체 안에 들어있는 데이터를 변수에 넣고 메세지로 띄워줌(Fprint)

vars := mux.Vars(r)
id, err := strconv.Atoi(vars["id"])

//ex) localhost:3000/users/1에 get 요청을 보내면 vars에 id값이 string으로 반환됨. string형으로 반환된 데이터를 int형으로 바꾸는 과정
```
