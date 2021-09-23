# SQL에서 null 값을 처리하는 법

## 개요
null 값을 처리한다의 의미는 만약 숫자 null이라면 산술연산을 할 때 0과 연산을 해야하는데 null과 연산하는 경우가 발생할 수 있다. 또한 테이블에 빈칸이 있는 것은 보기 좋지 않다. 한마디로 null이 아닌 다른 값을 얻고자 할 때 사용한다.

## 함수

IFNULL 함수 

사용법

```SQL
SELECT IFNULL(NAME,"no Name") from animal_ins
```

MYSQL에서의 NULL처리는 IF 함수로도 가능하다

```SQL
SELECT IF(IS NULL(NAME),"no name",NAME) as NAME
FROM ANIMAL_INS
```

COALESCE 함수도 있다.
```SQL
SELECT COALESCE(NAME,"no name")
FROM ANIMAL_INS
```