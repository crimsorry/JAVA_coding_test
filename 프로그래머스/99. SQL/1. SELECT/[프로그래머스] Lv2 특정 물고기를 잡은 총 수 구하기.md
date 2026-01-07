## 특정 물고기를 잡은 총 수 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/298518

### 내 코드

```SQL
SELECT COUNT(*) AS FISH_COUNT
FROM FISH_INFO A
    INNER JOIN FISH_NAME_INFO B ON A.FISH_TYPE = B.FISH_TYPE
WHERE B.FISH_NAME IN ('BASS', 'SNAPPER')
```



