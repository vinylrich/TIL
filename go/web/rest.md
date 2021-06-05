# Restful api
## Restful api in golang

---
목차
1. [What is Restful api?](#Restful-api란?)
2. [GET](#GET)
3. [POST](#POST)
4. [PUT](#PUT)
5. [DELETE](#DELETE)

___
## Restful-api란?
자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미.
![image](https://user-images.githubusercontent.com/51067720/120105299-524c0880-c193-11eb-9af6-e4ca01bfbbcc.png)
사진출처:https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html

한 사진으로 표현하자면 저 사진이 더할나위 없다.

___
## GET
`mux.HandleFunc("/users", usersHandler).Methods("GET") //users가 없으면 상위 핸들러가 호출됨`
users get 핸들러는 현재 모든 유저 리스트를 출력하는 핸들러이다.
```go
func usersHandler(w http.ResponseWriter, r *http.Request) {
	if len(userMap) == 0 {
		w.WriteHeader(http.StatusOK)
		fmt.Fprint(w, "No Users to Print")
		return
	}
	users := []*User{}

	for _, u := range userMap { //value값(구조체)을 넣음
		users = append(users, u)//users에 userMap에 있는 모든 값을 넣음
		fmt.Println(u)
	}

	data, _ := json.Marshal(users)
	w.Header().Add("Content-Type", "application/json")
	w.WriteHeader(http.StatusOK)
	fmt.Fprint(w, string(data))
}
```

`mux.HandleFunc("/users/{id:[0-9]+}", getUsersInfoHandler).Methods("GET")`
users/id get 핸들러는 id값에 해당하는 유저 정보를 출력하는 핸들러이다.
```go
func getUsersInfoHandler(w http.ResponseWriter, r *http.Request) {
	vars := mux.Vars(r)
	id, err := strconv.Atoi(vars["id"])
	if err != nil {
		w.WriteHeader(http.StatusBadRequest)
		fmt.Fprint(w, err)
		return
	}
	user, ok := userMap[id]
	if !ok {
		w.WriteHeader(http.StatusOK)
		fmt.Fprint(w, "No User Id:", id)
		return
	}
	w.WriteHeader(http.StatusOK)
	w.Header().Add("Contents-Type", "application/json")
	data, _ := json.Marshal(user)
	fmt.Fprint(w, string(data))
}
```
___
## POST
`mux.HandleFunc("/users", createUserHandler).Methods("POST")`
user post 핸들러는 body에 user 정보를 받아 usermap에 저장하는 핸들러이다.
```go
func createUserHandler(w http.ResponseWriter, r *http.Request) {
	user := new(User)
	err := json.NewDecoder(r.Body).Decode(user) //data받아오기
	if err != nil {
		w.WriteHeader(http.StatusBadRequest)
		fmt.Fprint(w, "Bad Request", err)
		return
	}

	user.CreateAt = time.Now()

	lastID++
	user.ID = lastID
	user.CreateAt = time.Now()
	userMap[user.ID] = user
	data, _ := json.Marshal(user) //
	w.Header().Add("content-type", "application/json")
	w.WriteHeader(http.StatusCreated)
	fmt.Fprint(w, string(data))
}
```


___
## PUT
`mux.HandleFunc("/users", updateUserHandler).Methods("PUT")`
user put핸들러는 body에 user정보를 받아 usermap을 수정하는 핸들러이다.	
```go
func updateUserHandler(w http.ResponseWriter, r *http.Request) {
	updateUser := new(User)
	/*
		{
			"id":%d,
			"first_name":"update"
		}
	*/
	err := json.NewDecoder(r.Body).Decode(updateUser)
	//decode:바디에서 json데이터 받아오기
	if err != nil {
		w.WriteHeader(http.StatusBadRequest)
		fmt.Fprint(w, err)
		return
	}
	//1번 id를 가지면
	//1번 id를 가진 user 구조체를 가져옴
	user, ok := userMap[updateUser.ID]
	/*
		{
			"first_name":"junwoo",
			"last_name":"kim",
			"email":"whktjd0109@gmail.com"
		}
	*/
	if !ok {
		updateUser.ID = 1
		w.WriteHeader(http.StatusOK)
		fmt.Fprint(w, "No User ID:", updateUser.ID)
		return
	}
	//실제로 client가 수정하고 싶은
	//부분만 수정 가능하게 만들기
	if updateUser.FirstName == "" {
		updateUser.FirstName = user.FirstName
	} //
	if updateUser.LastName == "" {
		updateUser.LastName = user.LastName
	}
	if updateUser.Email == "" {
		updateUser.Email = user.Email
	}
	data, _ := json.Marshal(updateUser) //
	w.Header().Add("content-type", "application/json")
	w.WriteHeader(http.StatusOK)
	fmt.Fprint(w, string(data))

}
```
____

## DELETE
`	mux.HandleFunc("/users/{id:[0-9]+}", deleteUserHandler).Methods("DELETE")`
users/id delete 핸들러는 id값에 해당하는 usermap을 delete하는 핸들러이다.
```go
func deleteUserHandler(w http.ResponseWriter, r *http.Request) {
	vars := mux.Vars(r)
	id, err := strconv.Atoi(vars["id"])
	if err != nil {
		w.WriteHeader(http.StatusBadRequest)
		fmt.Fprint(w, err)
		return
	}
	_, ok := userMap[id]
	if !ok {
		w.WriteHeader(http.StatusOK)
		fmt.Fprint(w, "No Delete User ID:", id)
		return
	}
	delete(userMap, id)
	w.WriteHeader(http.StatusOK)
	fmt.Fprint(w, "Deleted ID:", id)
}
```
지금껏 시청했던 강좌를 토대로 코드분석+함수를 정리하자!
	encode,decode,marshal,unmarshal,writeheader
	DefalutClient
	http.NewRequest
