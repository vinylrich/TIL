# Memory Garbage Collector(GC)

변수->메모리

변수 선언-> 값을 담는 그릇 생성

쓰지 않는 메모리를 버려줘야 함

c언어
```c
p = malloc(100);
free(p)
```
실수로 free를 안하면 메모리 쓰레기가 쌓임

## stack Memory
```c
if(..){
    int a;
}
```
중괄호 범위를 벗어나면 메모리를 없애버림(지역변수)
```c
if(){
    p=malloc(100)
    free(p)(o)
}
```
free(p)(x)
memory leak->bug


```go
func add(){
    var a int
    a=3
}
```
중괄호 바깥으로 넘어가면 쓸모가 없어짐

### Reference Count(참조된 횟수)가 0이 되면 메모리를 지우는 것
```go
func add()*int{
    var a int
    a=3
    var p *int
    p=&a
    return p
}
v:=add()
```
process
1. a 사라짐
2. p 참조 사라짐
3. v에 a 참조됨
4. a와 p참조가 끊어짐
5. p가 없어짐

### Reference Count의 문제점을 보완
외딴섬: 외부의 참조 없이 내부에서만 참조하면 gc가 없애줌
 

***but!*** gc는 속도가 느림
