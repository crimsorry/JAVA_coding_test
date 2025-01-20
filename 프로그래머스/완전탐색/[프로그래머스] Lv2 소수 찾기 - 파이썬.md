# 소수 찾기 - 파이썬

https://www.acmicpc.net/problem/10870



## 내 풀이

#### 문제 풀이 흐름

1. numbers 로 나올수 있는 조합을 구한다.
2. 각 조합 중 가장 큰 숫자를 구한다.
3. 소수 배열을 만든다. [False] * 가장 큰 숫자 + 1
4. 에라토스체의 원리를 이용해 소수를 구한다.
5. 각 조합에서 발생할 수 있는 소수의 갯수를 구한다.



#### 주요 포인트

`result = permutations(data, 3)`: 순열: data list 의 모든 조합 생성 

>  {a, b, c} {b, c, a}..



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAxMjBfMjQy/MDAxNzM3MzUzODQ4NDA0.QiwaJd6WcSB3EsQ-ao4xfUGccAvbQ1oAX46lOY0cAt8g.-QndJ1x-El6uYfDbLnSYJMVQOv321vnyIfViu4A2iVog.PNG/image.png?type=w773)



#### 내 코드

```python
from itertools import permutations

def solution(numbers):

    possible_numbers = set()
    for i in range(1, len(numbers) + 1):
        perms = permutations(numbers, i)
        for p in perms:
            num = int(''.join(p))
            possible_numbers.add(num)

    max_number = max(possible_numbers)

    sosu = [True] * (max_number + 1)
    sosu[0] = sosu[1] = False

    for i in range(2, int(max_number ** 0.5) + 1):
        if sosu[i]:
            for j in range(i * i, max_number + 1, i):
                sosu[j] = False

    asnwer = sum(1 for num in possible_numbers if sosu[num])

    return asnwer
```

