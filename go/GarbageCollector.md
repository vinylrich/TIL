# Memory Garbage Collector(GC)


메모리 구조

1. code memory
    - 실행할 프로그램의 코드 메모리
2. data memory
    - 전역변수,정적변수 메모리
3. [stack memory](#stack-memory)
    - 지역변수, 매개변수(함수)메모리
4. heap memory
    - 사용자가 직접 지정하는 메모리
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
go의 경우
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
1. p에 a 참조됨
2. v와 p 참조
3. v와 a 참조
4. p와 a참조 사라짐
5. p가 없어짐
6. 결론적으로 v와 a가 연결이 되고,p가 사라진 형태를 가짐
```c
*int add(){
    int a;
    a=3
    int* p
    p=&a
    return p
}
int *v=add()
```
process
1. p에 a 참조됨
2. v와 p 참조
3. v와 a 참조
4. a사라짐,p사라짐
5. 결론적으로 v가 아무것도 없는 값인 a를 참조하는 형태가 됨
why? reference count가 없기 때문
### Reference Count의 문제점을 보완
외딴섬: 외부의 참조 없이 내부에서만 참조하면 gc가 없애줌
 

***but!*** gc는 속도가 느림
요즘 Multi Thread를 이용하여 build과정에서 시간이 체감이 되지 않을정도로 조금씩 나눠서 collect함