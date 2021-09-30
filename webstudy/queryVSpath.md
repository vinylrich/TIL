# Query Param vs Path Param

## Query Param

query parameter는 path 뒤에 ?가 오는 것이다.

<b>/user?id=1</b>
```go
r.Get("/users",index)
func index(c* gin.Context){
    c.Query("id")
}

```

## Path Param
path parameter는 path 자체가 id가 되는것이다.

<b>/user/123</b>
```go
r.Get("/users/{id}")
```


## 각각 언제 사용해야 할까?
만약 어떤 자원을 식별하고 싶으면 Path Variable을 사용하고,
정렬이나 필터링을 한다면 Query Parameter를 사용하는 것이 Best Practice라고 한다. 
1. 옵셔널한 값이 있다면 Query param

2. Not found시, 404에러를 내려주길 원한다면 Path param

3. Not found시, 특정한 값을 내려주길 원한다면 Query param


