# 10.24 signup & signin with mongodb

## GCS개발

golang을 사용하여 개발하던 중, 
mongodb를 연결하여 회원가입과 로그인 기능을 구현하였다.

다음은 mongodb를 golang에 연결하는 함수이다.
```go
func GetDBCollection() (*mongo.Collection, error) {
	clientOptions := options.Client().ApplyURI("mongodb://localhost:27017")

	// Connect to MongoDB
	client, err := mongo.Connect(context.TODO(), clientOptions)
	if err != nil {
		return nil, err
	}
	// Check the connection

	err = client.Ping(context.TODO(), nil)
	if err != nil {
		return nil, err
	}
	collection := client.Database("GoLogin").Collection("users")
	return collection, nil
}

```
연결 양식은 client.Database("DATABASE명").Collection("컬렉션명")

mongodb vs mysql

database=schema

collection=table

가장 중요한 기능인 find 기능의 코드
```go
    filter := bson.M{"username": u.Username, "password": u.Password}
	collection, err := dblayer.GetDBCollection()
	err = collection.FindOne(context.TODO(), filter).Decode(&u)
```
fliter, 즉 password와 id가 같는지 확인하는 코드이다

insert 기능의 코드
```go
    if u.Email == "" || u.Password == "" {
		return &echo.HTTPError{Code: http.StatusBadRequest, Message: "invalid email or password"}
	}
	collection, err := dblayer.GetDBCollection()
	collection.InsertOne(context.TODO(), u)
```
공백인지 아닌지 판별 후 삽입
