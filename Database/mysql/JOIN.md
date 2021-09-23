# JOIN

## 개요
JOIN은 데이터베이스 내의 여러 테이블에서 가져온 레코드를 조합하여 하나의 테이블이나 결과 집합으로 표현해준다


## 종류

INNER 조인
LEFT OUTER, RIGHT OUTER, OUTER 조인
카티전 조인 (CROSS 조인)
셀프 조인

MySQL에서는 JOIN, INNER JOIN, CROSS JOIN이 모두 같은 의미로 사용됨

### INNER JOIN

INNER JOIN은 ON 절과 함께 사용되며, ON 절에 조건에 맞는 데이터만을 가져온다

INNER JOIN의 벤 다이어그램
![image](https://user-images.githubusercontent.com/51067720/134442682-4deff034-5134-4fa0-ba96-c0f91ffd1426.png)

구문 예시

```SQL
SELECT *

FROM Reservation, Customer

WHERE Reservation.Name = Customer.Name;

--INNER JOIN Reservation.Name = Customer.Name
```

### LEFT JOIN

![image](https://user-images.githubusercontent.com/51067720/134447340-50191a3b-f04a-44a6-961d-e0ae1a980ab1.png)

구문 예시
```SQL
SELECT *

FROM Reservation

LEFT JOIN Customer

ON Reservation.Name = Customer.Name

WHERE ReserveDate > '2016-02-01';
```
