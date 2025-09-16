# 베스트앨범 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/42579



## 내 풀이

#### 문제 풀이 흐름

1. 반복문을 순회하며 dic1 에 각 장르별 인덱스번호와 플레이 횟수, dic2 에 각 장르별 총 플레이 수를 구한다.
2. 플레이 수가 가장 큰 장르에서 플레이 횟수가 가장 큰 앨범을 최대 2장까지 인덱스 번호를 구한다.



#### 주요 포인트

`zip(t1, t2)`: 배열 t1, t2 모두 순회하면서 요소 출력. t1, t2 길이 다르면 작은 길이를 기준으로 순회.
`enumerate(zip(t1, t2))` : 각 배열을 순회하면서 enumerate 로 인덱스도 가져옴



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAxMjBfMTQy/MDAxNzM3MzUyNTU3NDAz.ETvt8y0OazCNUg4ycY7UHsLkCwapHHnKjMf2a0utCf8g.qWfGfoy6uDsnMbfmOlzLKQ976x8Napdyz1_OqQSLkz0g.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(genres, plays):
    answer = []
    
    dic1 = {}
    dic2 = {}
    
    for i, (g, p) in enumerate(zip(genres, plays)):
        if g not in dic1:
            dic1[g] = [(i, p)]
        else:
            dic1[g].append((i, p))
            
        if g not in dic2:
            dic2[g] = p
        else:
            dic2[g] += p
            
    for (k, v) in sorted(dic2.items(), key=lambda x:x[1], reverse=True):
        for (i, p) in sorted(dic1[k], key=lambda x:x[1], reverse=True)[:2]:
            answer.append(i)
    
    return answer
```



