# 명령 프롬프트 - 파이썬

https://www.acmicpc.net/problem/1032



## 내 풀이

#### 문제 풀이 흐름

1. 첫번째 단어와 두번째 단어가 일치하는지 확인한다.
2. 일치하는 문자를 array 배열에 삽입한다. 일치하지 않으면 ? 를 넣는다.
3. 계속 반복한다.
4. 만약 n 이 1이라면 첫번쨰 단어를 그대로 반환한다.



#### 주요 포인트

* **list(answer)** : 문자열을 list 로 변환할 수 있다.



#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMjdfNjMg/MDAxNzM1MjMyMTI5Nzgy.mPzOoLCP7WK9QdM7t8gXj3yTxie8dgYwighIxk4zJs8g.tAXq6DiGq-3X6R80P26GQ2wAxQsqG_tca6kkD6KRyL0g.PNG/image.png?type=w773)



#### 내 코드

```python
n = int(input())
answer = ""

for i in range(n):
    file = input()
    if i == 0:
        answer = file
        continue
    answer = list(answer)
    for j in range(len(file)):
        if answer[j] == '?':
            continue
        elif file[j] != answer[j]:
            answer[j] = '?'
    answer = ''.join(answer)

print(answer)
```

