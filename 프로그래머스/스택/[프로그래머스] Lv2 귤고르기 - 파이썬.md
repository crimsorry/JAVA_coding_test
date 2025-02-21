# 귤고르기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/138476

## 내 풀이

#### 문제 풀이 흐름

1. 귤의 크기, 크기 별 귤의 갯수 를 담은 배열 선언
2. 귤의 갯수가 큰 순서대로 정렬
3. k 수 만큼 빼기



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAzMDNfMTk3/MDAxNzQwOTg4MzU2OTEx.zGAQMDe61e8kNW7uzcNd6xFl0GH6eLwkZH_sKvoZiO4g.mzH9qF4mF8JTB2qES9Fz4ZQalrZfHzvwWzJclG3hX4Mg.PNG/image.png?type=w773)



#### 내 코드

```python
from collections import Counter

def solution(k, tangerine):
    answer = 0
    
    count = Counter(tangerine)
    sorted_count = sorted(count.values(), reverse=True)
    
    total = 0
    
    for c in sorted_count:
        total += c
        answer += 1
        if total >= k: 
            break
            
    return answer
```



