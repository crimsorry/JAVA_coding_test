# 영어 끝말잇기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/12981



## 내 풀이

#### 문제 풀이 흐름

1. Counter 로 중복된 단어가 있는지 구하기
2. 중복된 단어가 없다면 [0, 0] return
3. 중복된 단어가 없지만, 앞뒤 단어가 다른경우 찾기
3. 중복된 단어가 있다면 enumerate() 를 이용해 몇번째 단어가 위치하는지 찾기



#### 결과

![image.png](https://blogfiles.pstatic.net/MjAyNTAzMDNfODUg/MDAxNzQwOTkxOTk5MzMw.GS8I5K15qbtPE_cIShSZRVR1BDsL2pfFIuWYC8HR9XIg.4Td9j80mgFVFI-0yl6W4lBApDEe2cHte5c29GKAOvIMg.PNG/image.png?type=w1)





#### 내 코드

```python
def solution(n, words):
    used_words = set()
    
    for i, word in enumerate(words):
        person = (i % n) + 1
        turn = (i // n) + 1
        
        if i > 0 and words[i-1][-1] != word[0]:
            return [person, turn]
        
        if word in used_words:
            return [person, turn]
        
        used_words.add(word)
        
    return [0, 0]
```



#### 다른 사람 풀이

```python
def solution(n, words):
    for i in range(1, len(words)):
        if words[i][0] != words[i-1][-1] or words[i] in words[:i] :
            return [(i%n)+1, (i//n)+1]
    else:
        return [0,0]
```

* 1부터 시작하는 range 를 이용해 코드 간략화
* or 연산을 사용해 코드 블럭 간략화