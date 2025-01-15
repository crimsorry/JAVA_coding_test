# 시소 짝꿍 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/152996?language=python3



## 내 풀이

#### 문제 풀이 흐름

1. 이중 for 문을 이용해 i weight 와 j wdight 를 비교한다.
2. 중심으로부터 2, 3, 4 지점에 위치할 경우의 수를 구한다.
3. 시소 짝궁 = weight * 좌석간의 거리
4. 시소 짝궁이라면 result +1 시킨다.



#### 문제상황

문제에 나와있는 요구사항대로 풀어보니 시간초과 에러 발생.

> 시간 초과 해결을 위해 **딕셔너리** 사용!

##### 새로운 해결방법

1. 같은 몸무게가 몇번 등장했는지 저장
2. 가능한 비율 찾기

```
possible_ratios = [2/2, 3/2, 4/2, 3/3, 4/3, 4/4]
```

3. 같은 몸무게끼리 시소 짝꿍 찾기
4. 다른 몸무게끼리 시소 짝꿍 찾기

```markdown
비율: 3/2 > 1.5 일때
target_weight = 180 * 1.5 = 270

따라서 180 은 270 과 짝꿍이 된다!
```



#### 주요 포인트

```python
from collections import Counter

# 빈도 개산
counter = Counter(weights)

# 중복 제거
set_weights = set(weights)
```



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAxMTVfMjY2/MDAxNzM2OTQ2MzAwNzY0.BWqjzXcXkZBU5Ja5GHmlaudnY-XiJ3WUpNUAbHFSangg.N5OFAKIUVuanmgj4162VmSRd2JOZyWwF_1xCVcX8O1Qg.PNG/image.png?type=w773)



#### 내 코드

```python
from collections import Counter

def solution(weights):
    answer = 0
    counter = Counter(weights)

    for k, v in counter.items():
        if v >= 2:
            answer += v * (v - 1) // 2

    set_weights = set(weights)

    for w in set_weights:
        if w * 2 / 3 in set_weights:
            answer += counter[w * 2 / 3] * counter[w]
        if w * 2 / 4 in set_weights:
            answer += counter[w * 2 / 4] * counter[w]
        if w * 3 / 4 in set_weights:
            answer += counter[w * 3 / 4] * counter[w]
    return answer
```



#### 오류 코드

```python
def solution(weights):
    answer = 0

    for i in range(0, len(weights)):
        for j in range(i+1, len(weights)):
            if weights[i] == weights[j]:
                answer += 1
            elif weights[i] * 2 == weights[j] * 3:
                answer += 1
            elif weights[i] * 3 == weights[j] * 2:
                answer += 1
            elif weights[i] * 2 == weights[j] * 4:
                answer += 1
            elif weights[i] * 4 == weights[j] * 2:
                answer += 1
            elif weights[i] * 3 == weights[j] * 4:
                answer += 1
            elif weights[i] * 4 == weights[j] * 3:
                answer += 1
    return answer
```

