## 뒤집기 - 파이썬

https://www.acmicpc.net/problem/1439



## 내 풀이

#### 문제 풀이 흐름

1. 문자열을 입력받는다
2. 배열을 초기화하고 문자열의 첫번째 받는 변수를 선언한다
3. 반복문을 통해 연속된 문자열이 변경되는 경우 array 에 값을 저장한다.
4. array 에서 작은 값을 출력한다.



#### 주요 포인트

* `min()` : 작은 값을 구할 수 있다.



#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMTRfNjUg/MDAxNzM0MTY5NjYyMzU1.xWH1sCi7kZM67jjyfn4wQWfMo56dwMcMI2kHuNdpjeog.E7MMwtStnAb0t6WKDdrvw7rl_mA9wzoyYe5zA3XHgCYg.PNG/image.png?type=w773)



#### 내 코드

```
s = input()

array = []
first_one = s[0]
array.append(first_one)
for i in s:
    if i != first_one:
        first_one = i
        array.append(first_one)

print(min(array.count('0'), array.count('1')))
```

