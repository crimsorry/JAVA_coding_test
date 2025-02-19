# 짝지어 제거하기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/12973?language=python3



## 내 풀이

#### 문제 풀이 흐름

1. stack 에 문자열 담기
2. 현재 문자열과 stack 의 마지막 문자열의 값이 일치하면 pop
3. 현재 문자열과 stack 의 마지막 문자열의 값이 일치하지 않으면 append
4. stack 이 비어있으면 1
5. stack 이 비어있지 않으면 0



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAzMDFfNDAg/MDAxNzQwODA0NTQ5OTgz.yOZmnIAREel0DaA81CoE91JMyNfkMSCwDzCNs5JScqgg.Y28qyTG-6H8C5reZO7ub2Z2A-r9-WIt_R3qviAn--hAg.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(s):
    stack = []

    for value in s :
        if not stack :
            stack.append(value)
        else :
            if stack[-1] == value :
                stack.pop()
            else :
                stack.append(value)  

    if stack :
        return 0

    return 1
```


