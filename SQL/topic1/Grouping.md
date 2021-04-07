# Grouping

특정 속성들을 기준으로 값이 같은 행들을 묶어서 질의처리 할 수 있다.

Default로 모든 행들이 한 group이었다고 생각할 수 있다.

기본 형태: 

```sql
GROUP BY (grouping 기준)
HAVING
```

- Aggregate function(집계함수)을 사용하면 각 그룹마다 함수가 호출된다.

  ```sql
  SELECT
     SUBSTRING(address, 1, 2) AS region,
     COUNT(*) // 이 집계함수는 각 그룹에 대해 실행된다
  FROM member
  GROUP BY SUBSTRING(address, 1, 2)
  ```
  
  결과
  
  <img width="105" alt="스크린샷 2021-04-07 오후 7 54 18" src="https://user-images.githubusercontent.com/61934702/113855601-305d8780-97db-11eb-845c-512dcffe7659.png" width = "60%">

  
- grouping 기준을 여러개로 설정할 수 있다

  GROUP BY 기준1, 기준2, 기준3...
  
  각 기준에 따라
