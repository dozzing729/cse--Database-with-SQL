# Grouping

## GROUP BY

특정 속성들을 기준으로 값이 같은 행들을 묶어서 질의처리 할 수 있다.

Default로 모든 행들이 한 group이었다고 생각할 수 있다.

기본 형태: 

```sql
GROUP BY (grouping 기준)
HAVING
```

- **Aggregate function(집계함수)을 사용하면 각 그룹마다 함수가 호출된다.**

  ```sql
  SELECT
     SUBSTRING(address, 1, 2) AS region,
     COUNT(*) // 이 집계함수는 각 그룹에 대해 실행된다
  FROM member
  GROUP BY SUBSTRING(address, 1, 2)
  ```
  
  결과
  
  <img width="105" alt="스크린샷 2021-04-07 오후 7 54 18" src="https://user-images.githubusercontent.com/61934702/113855601-305d8780-97db-11eb-845c-512dcffe7659.png" width = "60%">

  
- **grouping 기준을 여러개로 설정할 수 있다**

  GROUP BY 기준1, 기준2, 기준3...
  
  먼저 적힌 기준이 더 우선순위가 높다. 우선 순위가 높은 기준부터 차례대로 grouping을 수행한다.
  
  ```sql
  SELECT 
	SUBSTRING(address, 1, 2) as region,
    gender,
	COUNT(*)	
  FROM dozzing_inc.member
  GROUP BY 
	SUBSTRING(address, 1, 2),
    gender
  ORDER BY region
  ```
  
  결과: region을 기준으로 먼저 그루핑되고, 각 region마다 gender를 기준으로 다시 그루핑 된 것을 확인할 수 있다
  
  <img width="146" alt="스크린샷 2021-04-07 오후 7 58 35" src="https://user-images.githubusercontent.com/61934702/113856537-5899b600-97dc-11eb-8a26-ad5a7220e0d0.png" width = "60%">
  


## HAVING
