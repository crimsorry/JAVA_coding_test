# n^2 배열 자르기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/87390



## 내 풀이

#### 문제 풀이 흐름

1. 몇번째 행에 좌표가 존재하는지 확인 i // n
2. 몇번째 열에 좌표가 존재하는지 확인 i % 2



#### 주요 포인트

탐욕법으로 문제를 풀게 되면 시간복잡도 문제가 날 수 있다.



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAzMDZfMTQ4/MDAxNzQxMjU2ODQzMDU5.zWFX4aDPyhPeACrDab0eaS35h6A_JUhEFX75JvL_mMYg.a0J8Y41Omq77afAL3s7nOmv4hH0DbXGQh_jOX0dgbRsg.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(n, left, right) :
    answer = []
    for i in range(left, right + 1) :
        answer.append(max(i//n, i%n) + 1)

    return answer
```


