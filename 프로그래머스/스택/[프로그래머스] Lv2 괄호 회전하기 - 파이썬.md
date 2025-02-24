# 괄호 회전하기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/76502



## 내 풀이

#### 문제 풀이 흐름

1. len(s) 만큼 반복문 돌리기
2. arr 배열에 s 를 회전시킨 배열 넣기
3. 각 arr 배열이 올바른 괄호 문자열인지 확인하기



#### 주요 포인트

* stack 의 pop 은 O(1) 시간복잡도를 가진다.



#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAzMDRfMjg1/MDAxNzQxMDgzNzk5Mzkz.sKavvhUmH_Oei7Ru6jsr8zDN-AFBoIHNIVCn5EIVOfUg.i1Z5cjYTd27rL9vrYbi-WXTASSy3bjm5TpRuTM9maTsg.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(s):
    answer = 0
    
    for i in range(len(s)):
        arr = s[i:] + s[0:i]
        stack = []
        
        for j in arr:
            if not stack:
                stack.append(j)
            else:
                if j == ']' and stack[-1] == '[':
                    stack.pop()
                elif j == ')' and stack[-1] == '(':
                    stack.pop()
                elif j == '}' and stack[-1] == '{':
                    stack.pop()
                else:
                    stack.append(j)
        
        if not stack:
            answer+=1
    
    return answer
```



