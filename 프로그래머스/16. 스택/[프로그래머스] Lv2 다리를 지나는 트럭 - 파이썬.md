# 다리를 지나는 트럭 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/42583



## 내 풀이

#### 문제 풀이 흐름

1. loop 를 순회하며 시간을 증가시킨다.
2. 만약 현재 올라온 트럭의 무게가 weight 보다 크다면 deque 배열에 0 을 삽입한다. (더 이상 못 올라오기 때문)
3. 그렇지 않다면, deque 배열에 truck_weights 의 첫번째 원소를 삽입하고, 현재 무게를 증가시킨다.
4. loop 를 빠져나온 뒤 time 에 다리 길이를 더한다



#### 주요 포인트

* truck_weights 순서를 뒤집어 queue 와 같이 사용한다.

  > **why?**
  >
  > python에서 리스트의 **첫 번째 원소를 `pop(0)`로 꺼내는 연산은 O(n)**이지만, **마지막 원소를 `pop()`로 꺼내는 연산은 O(1)**
  >
  > 따라서 `truck_weights.reverse()`를 사용해 리스트를 뒤집은 뒤, 마지막 원소를 꺼내는 방식으로 **성능 최적화**



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAxMjBfMjkw/MDAxNzM3MzUyNzIwMTc3.7f8wzZbYstaL7Pzf2Em8t_ph0YA2qcKU60ck5TAB6Kwg.Ff1Q_kexUnHRj5c54BoF65bThAaOS-77-SbpOAPR6Wwg.PNG/image.png?type=w773)



#### 내 코드

```python
from collections import deque
def solution(bridge_length, weight, truck_weights):
    bridge = deque([0] * bridge_length)
    total_weight = 0
    time = 0
    truck_weights.reverse()

    while truck_weights:
        time += 1
        total_weight -= bridge.popleft()
        if total_weight + truck_weights[-1] > weight:
            bridge.append(0)
        else:
            truck = truck_weights.pop()
            bridge.append(truck)
            total_weight += truck

    time += bridge_length

    return time
```



