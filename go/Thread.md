# Thread

## 등장배경

1. 옛날에는 cpu 코어가 하나였다.
2. 여러개를 돌리려면 하나의 cpu 코어로 여러 프로세스를 돌려야 했다.
3. 1번 프로세서에서 2번 프로세서로 바꾸는 것을 context switching이라고 한다.
4. thread를 너무 많이 만들면 context switching이 커져서 효율이 떨어진다

kernel thread->wrapping->GoThread

os thread 최소한 사용

//cpu < Thread
context switching이 일어남
cpu갯수만큼 thread를 만들고 각 os를 잘게 잘라서 여러개의 go thread를 만듦
go 내부에서 os thread kernel thread 를 알아서 할당해주기 때문에 thread 개수에 상관하지 않아도 된다.


1. program=app
2. process=app이 실행돼서 cpu에서 돌아가는 상황
3. thread=process는 여러개의 thread 아래에서 돌아감

syncronize
memory

lock과 channel 둘 중 하나를 쓸 수 있음
