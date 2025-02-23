# 예상 대진표 - 파이썬

https://www.acmicpc.net/problem/10870



## 내 풀이

#### 문제 풀이 흐름

1. 짝수라면 나눈값이 현재 라운드, 홀수라면 나눈값+1 이 현재 라운드
2. a 와 b 의 현재 라운드 값이 같다면, ans-1





#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAzMDNfMTEw/MDAxNzQxMDA3NzQ4MzIz.1R0jmlKh3CcspDsrS3kZmFIADHcVbQ1Q1D8AFWCw2LYg.zp6OKTAwAwk7x4D0LpnTuDOPpCyzg5IkdVKJL46meJog.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(n,a,b):
    
    answer = 0;
    
    while True:
        answer+=1
        
        if a%2==1:
            a = a//2+1
        else:
            a = a//2
        if b%2==1:
            b = b//2+1
        else:
            b = b//2
            
        if a==b:
            break;
    
    return answer
```



