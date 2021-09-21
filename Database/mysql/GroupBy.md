# GroupBy란

GROUP BY란 X를 기준으로 결과값을 묶는 것이다.
예를 들어 같은 동물을 기준으로 개수를 구해야 한다고 생각해보자.
```sql
SELECT ANIMAL_TYPE,COUNT(ANIMAL_TYPE)
FROM ANIMAL_OUTS
GROUP BY ANIMAL_TYPE
```
와 같이 쿼리를 짤 수 있다.
![image](https://user-images.githubusercontent.com/51067720/134190856-8240cf84-a833-429e-8782-3fa3aa6afa70.png)

원하는 결과값인 dog와 cat을 기준으로 dog cat 개수를 구하는 결과가 나온다.

하나의 예시를 더 들어보자.

동물들이 중성화 수술을 했는지 여부를 구해보자.

```sql
SELECT SEX_UPON_OUTCOME,COUNT(SEX_UPON_OUTCOME)
FROM ANIMAL_OUTS
GROUP BY SEX_UPON_OUTCOME
```

쿼리는 이런식으로 짤 수 있다.

![image](https://user-images.githubusercontent.com/51067720/134191174-6ede6519-46ef-417c-94b6-81bc42f017bf.png)

우리가 원하는 결과값인 중성화 수술 종류,여부를 알 수 있다.

GROUP BY에서 빼 놓을 수 없는 구문은 바로 <B>HAVING</B>구문이다.

중성화 수술 여부 중 "Neutered Male"만 보고 싶다 하면

```sql
SELECT SEX_UPON_OUTCOME,COUNT(SEX_UPON_OUTCOME)
FROM ANIMAL_OUTS
GROUP BY SEX_UPON_OUTCOME
HAVING SEX_UPON_OUTCOME="Neutered Male"
```
와 같은 쿼리를 짤 수 있다.
![image](https://user-images.githubusercontent.com/51067720/134191664-8a9c64bf-5821-4199-bd9c-4ec95b937ddf.png)

HAVING은 WHERE절과 상당히 유사한데, GROUP BY를 해서 나온 테이블에 WHERE절을 붙인다고 이해하면 쉽다.