# 타겟 넘버 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/43165?language=python3



## 내 풀이

#### 문제 풀이 흐름

1. 재귀함수를 선언한다
2. current_sum 을 더하는 경우, 빼는 경우를 재귀를 이용해 호출한다
3. 만약 current_index 가 numbers 의 길이와 같고
   1. target 과 current_sum 이 같다면
      1. 결과 값을 +1 갱신한다.



#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMjNfOTMg/MDAxNzM0ODg2NzQ0NDU5.SLOMlPMVxzTNOJqBR2jkbp8wSX1z3eEKIVFQrpJV_Rgg.DTCt4kDi6xVbvUPqWiyfZRNKSV5FfyqdR6qo6uCh1eUg.PNG/image.png?type=w773)



#### 내 코드

```python
result_count = 0

def solution(numbers, target):
    get_plus_minus(numbers, target, 0, 0)
    return result_count

def get_plus_minus(numbers, target, current_index, current_sum):
    if current_index == len(numbers):
        if target == current_sum:
            global result_count
            result_count += 1
        return
    get_plus_minus(numbers, target, current_index+1, current_sum + numbers[current_index])
    get_plus_minus(numbers, target, current_index+1, current_sum - numbers[current_index])
```



