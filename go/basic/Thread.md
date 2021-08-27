# Thread

### 1. [Why thread](#Why-Thread)
### 2. [Multi Thread](#Multi-Thread)
### 3. [Program,Process,Thread](#Program,Process,Thread)
### 4. [Thread in Go](#Thread-in-Go)
### 5. [vs c++,c#,java](#vs-c++,-c#,-java)
----

## Why Thread

옛날에는 cpu 코어가 하나였다.<br>
여러개를 돌리려면 하나의 cpu 코어로 여러 프로세스를 돌려야 했다.<br> 하지만 코어의 수를 늘리는 것은 한계가 있기 때문에 하나의 코어에 여러개의 쓰레드를 만들어 여러 프로세서를 실행할 수 있게 했다.

____
## Multi Thread
1. 한 코어에서 여러개의 프로세스를 돌린다는 장점이 있듯이, 이도 단점이 있다.
2. 1번 프로세서에서 2번 프로세서로 바꾸는 것을 context switching이라고 한다.
3. thread를 너무 많이 만들면 context switching이 커져서 context switching을 할 때 자원이 들기 때문에 효율이 떨어진다.
______
## Program,Process,Thread

1. program=app
2. process=app이 실행돼서 cpu에서 돌아가는 상황
3. thread=process는 여러개의 thread 아래에서 돌아감
____
## Thread in Go

go에서는 자체적인 thread 시스템을 제공한다. 사용할때는 그냥 단순히 go 키워드만 사용하면 되지만, 더 세부적인 사항을 정리했다.

kernel thread: os가 제공하는 기본적인 thread

이 kernel thread를 wrapping(포장) 해서 만든 것=Go Thread

### 왜 wrapping 했냐?
1. os thread를 많이 사용하면 context switching이 많이 일어남<br>

2. 그러니 os thread를 최소한으로 사용

3. go 키워드를 사용하면 cpu갯수와 가깝게 os thread를 만들고 각 os를 잘게 잘라서 여러개의 go thread를 만듦
4. go 내부에서 os thread kernel thread 를 알아서 할당해주기 때문에 개발자는 thread 개수에 상관하지 않아도 된다.

___
## vs c++,c#,java
c++과 c#과 java는 하나의 thread가 하나의 os영역에 1:1 대응하고있음
따라서 thread를 많이 만들면 context switching이 아주 많이 일어남

물론 c#이나 java는 thread pool이 있긴 하지만 go에서는 바로 go 키워드만 사용하면 알아서 개수 상관하지 않고 효율적으로 만들어주기 때문에 더 편리하고 go의 최대 강점이라고 할 수 있다.

syncronize(동기화) 문제