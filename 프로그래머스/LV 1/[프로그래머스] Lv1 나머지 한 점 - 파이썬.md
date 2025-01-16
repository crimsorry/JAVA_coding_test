# 나머지 한 점 - 파이썬

https://school.programmers.co.kr/learn/courses/18/lessons/1878?language=python3



## 내 풀이

#### 문제 풀이 흐름

1. 반복문을 돌며 x 와 y 좌표 값 저장하기
2. 빈도값이 1 인 좌표 값을 찾아 return 하기

* 저번에 알게 된 collections 를 이용해 풀이해보기!



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAxMTdfMTc0/MDAxNzM3MTE4NDU5MzY2.OSGAb1nY5RP_Ziw4Mq3KFBP9G5g_zrutPYQj2WVtOIUg.OZRzrpVk7jgpOdAl2-WJqkmsu2P-IxjZDtEbtBNQbT8g.PNG/image.png?type=w773)



#### 내 코드

```python
from collections import Counter

def solution(v):
    answer = []
    x = []
    y = []

    for i in range(len(v)):
        x.append(v[i][0])
        y.append(v[i][1])

    count_x = Counter(x)
    count_y = Counter(y)

    unique_x = [k for k, v in count_x.items() if v == 1]
    unique_y = [k for k, v in count_y.items() if v == 1]

    answer = unique_x + unique_y

    return answer
```
