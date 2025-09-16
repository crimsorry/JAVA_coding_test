# K번째수 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/42748?language=python3



## 내 풀이

#### 문제 풀이 흐름

1. 반복문을 돌린다. len(commands)
2. array 에서 commands[0] , commands[1] 사이값에 해당하는 배열을 복사한다. copy_array
3. copy_array 를 정렬한다.
4. 정렬한 배열에서 commands[2] 값을 구한다.
5. answer 배열에 추가한다.



#### 주요 포인트

* **array[0:3]** : 배열 쪼개기
* **copy_array.sort()**: 정렬



#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMjRfMjQw/MDAxNzM1MDQ5NjU4MTA0._p78dJhvF-hn8Ku0PuV_79nzkUuHl4QcqSFWpgrSvLwg.VeimQJnM7rsAyoOHKXTbH00-KXmDmJ1-5Phhy63G9wAg.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(array, commands):
    answer = []
    for sub in commands:
        copy_array = array[sub[0]-1:sub[1]]
        copy_array.sort()
        answer.append(copy_array[sub[2]-1])
    return answer
```

