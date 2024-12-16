# 요세푸스 문제 - 파이썬

https://www.acmicpc.net/problem/1158



## 내 풀이

#### 문제 풀이 흐름

1. 배열에 n 순차적으로 값을 넣는다.
2. 반복문을 돌려 k 번째 수를 정답 배열에 넣는다



#### 문제상황

* O(N*N): 자바로 이중 for 문을 사용했을때는 정상적인 결과가 나왔지만, python 의 경우 시간초과가 나왔다. 따라서 O(N) 시간복잡도 내에서 풀수 있도록 Deque 를 이용해 문제를 해결하였다.



#### 주요 포인트

* **deque(range(1, n+1)):** 양쪽 끝에 원소를 삽입/제거할 수 있는 양방향 Queue
* **", ".join(map(str, answer))**: array print



#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMjJfMjM0/MDAxNzM0NzkzMzk5NTg0.sjVS6aZIof6SzjuCVc4CGfsZTSbqVSSFOWTFvr0FXzgg.2kP4iWczl2dhGG1iWotrWRMIqwJiLpoCI-o-vOM1l0Mg.PNG/image.png?type=w773)



#### 내 코드

```python
from collections import deque

n, k= map(int, input().split())

q = deque(range(1, n+1))
answer = []

while q:
    q.rotate(-(k - 1))
    answer.append(q.popleft())

print("<" + ", ".join(map(str, answer)) + ">")
```





#### 시간초과

```python
while len(array) != 0:
    for i in range(1, k):
        array.append(array.pop(0))
    answer.append(array.pop(0))
```

