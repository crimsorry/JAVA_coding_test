# 특정 기간동안 대여 가능한 자동차들의 대여비용 구하기 

https://school.programmers.co.kr/learn/courses/30/lessons/157339



## 내 풀이

#### 주요 포인트

* history 테이블은 대기 중인 자동차 목록을 나타내는 테이블이다.
* 따라서 대여 가능한 차의 목록을 알기 위해선, 대여 원하는 시간에 history 테이블에 **존재하지 않은 자동차ID**를 알아야 한다.

```SQ
round( )                    -- 소수점 반올림 ex) 1235.12 > 1235 / 1235.98 > 1236
CAR_TYPE IN ('세단',  'SUV') -- 세단 이거나, SUV 인 경우
```



#### 내 코드

```SQL
SELECT c.CAR_ID, c.CAR_TYPE, ROUND(c.DAILY_FEE*30*(100-p.DISCOUNT_RATE)/100) AS FEE
FROM CAR_RENTAL_COMPANY_CAR c 
     LEFT JOIN CAR_RENTAL_COMPANY_RENTAL_HISTORY h ON c.CAR_ID = h.CAR_ID 
     LEFT JOIN CAR_RENTAL_COMPANY_DISCOUNT_PLAN p ON c.CAR_TYPE = p.CAR_TYPE
WHERE C.CAR_ID NOT IN ( 
        SELECT CAR_ID
        FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
        WHERE END_DATE >= '2022-11-01' AND START_DATE <= '2022-12-01')
      AND p.DURATION_TYPE like '30%'
GROUP BY c.CAR_ID
HAVING c.CAR_TYPE IN ('세단',  'SUV') AND FEE >= 500000 AND FEE < 2000000
ORDER BY FEE DESC, c.CAR_TYPE, c.CAR_ID DESC
```



