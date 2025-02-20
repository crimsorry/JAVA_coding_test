# 점프와 순간 이동 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/12980



## 내 풀이

#### 문제 풀이 흐름

1. 반복문을 돌려 홀수가 되는 경우 정답을 1 씩 추가한다. (홀짝)



#### 주요 포인트

그리디를 이용한 풀이



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAzMDFfMTE1/MDAxNzQwODA1NTQ0MDgz.h4iBCD7kLtgo6eQOR_vfgSTjDHMblC0Hgfj9ktDGZdUg._fmr7gXwCkzsq_XbCt05CnXh4zJ-odogvh0bJlSyDJgg.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(n):
    answer = 0
    while n > 0:
        if n % 2 == 0:
            n = n // 2
        else: 
            n = n - 1
            answer += 1
    
    return answer
```



