# 두 큐 합 같게 만들기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/118667



## 내 풀이

#### 문제 풀이 흐름

1. 각 queue 를 deque 에 삽입
2. 두 deque 의 합이 홀수라면 return -1
3. sum1 이 sum2 보다 작으면 deque2 에 deque1.popleft()
4. sum2 가 sum1 보다 작으면 deque1 에 deque2.popleft()
5. sum1 과 sum2 가 같으면 return ans



#### 문제상황

모든 경우의 수를 구해야 하지 않을까? 에 빠져 문제 해결과정을 찾는데 시간이 오래 걸렸다... 

검색을 통해 해당 문제는 '투 포인터' 문제로 최적의 과정에서 정답을 찾는 문제라는 것을 깨닫게 되었다.



#### 주요 포인트

**투 포인터(Two Pointers)**

 "연속된 데이터 구조(배열, 문자열 등)에서 최적의 해를 찾는 문제"

* 두 개의 포인터(인덱스)를 사용하여 배열을 탐색하면서 해를 찾음
* 정렬된 배열에서 최적의 값(예: 구간합, 최대/최소 길이 등)을 찾는 문제에서 주로 사용됨
* 한 번의 탐색(while, for)을 통해 O(N) 이하로 해결할 수 있는 경우 유리



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAzMDVfNDAg/MDAxNzQxMTc4MDM3NzQz.ZMsceHiAFDy7jy1P3ZWe9kpvPQo1KkOmvoEUDqR9u9cg.3dc6kqQvSb2rYrN-RKyu8_H8phJDHS9KXjzcn-x11AAg.PNG/image.png?type=w773)



#### 내 코드

```python
from collections import deque


def solution(queue1, queue2):
    
    deque1 = deque(queue1)
    deque2 = deque(queue2)
    
    answer = 0
    sum1 = sum(deque1)
    sum2 = sum(deque2)
    
    if (sum1 + sum2) % 2 != 0:
        return -1
    
    limit = 4 * len(queue1)
    
    while answer < limit:
        if sum1 > sum2:
            d1 = deque1.popleft()
            deque2.append(d1)
            sum1 -= d1
            sum2 += d1
        elif sum1 < sum2:
            d2 = deque2.popleft()
            deque1.append(d2)
            sum1 += d2
            sum2 -= d2
        else:
            return answer
        answer += 1
    
    return -1
```



