# 소수 찾기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/12921



## 내 풀이

#### 문제 풀이 흐름

1. 에라토스체의 원리를 이용한다.
2. 이중 반복문을 돌린다.
3. 첫번째 반복문은 n 까지 돌린다.
4. 두번째 반복문은 i 의 제곱근까지 돌린다.
5. i 와 j 를 나눈 나머지가 0 이라면 소수가 아니다.





#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMjRfMTUx/MDAxNzM1MDUxNjUyODkx.oBqya4FoiIk8OaQgWtNFunn8lgfzD8mCuKniuYeXRCgg.lXFirQ8iDZdLqErzk2vMxQfUNG3Sp3V5GUfYP0fDJtQg.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(n):
    answer = 0
    for i in range(2, n+1):
        is_decimal = True
        for j in range(2, int(i**0.5)+1):
            if i % j == 0:
                is_decimal = False
                break
        if is_decimal:
            answer += 1
    return answer
```



