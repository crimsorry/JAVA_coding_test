# 기능 개발 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/42586?language=python3



## 내 풀이

#### 문제 풀이 흐름

1. time, count 변수를 선언한다.
2. process 가 0 이 되기 전까지 loop 를 돌린다.
3. progresses[0] + (time*speeds[0]) 이 100보다 크거나 같다면 count 를 증가시키고, progress[0], speeds[0] pop 한다.
4. 만약 그렇지 않다면, time 을 증가시킨다.
5. 만약 count>0 라면, 정답 배열에 count 를 추가하고, count 를 초기화 시킨다.



#### 주요 포인트

`stack.pop()`: 마지막 번째 원소 없애기. (DFS(깊이 우선 탐색), 수식 계산, 괄호 검사)

`queue.popleft()`: 첫번째 원소 없애기. (BFS(너비 우선 탐색), 캐시 구현 등)

`priority_queue.heappop(pq)`: 최소값 제거. (다익스트라 알고리즘, K번째 최소/최대값 찾기 등)





#### 결과

![img](https://postfiles.pstatic.net/MjAyNTAxMjBfOTUg/MDAxNzM3MzUxODk1ODI1.HCG6jrED-7_d52O5iBxmxKKuAZxRnMvyCpfvFJdIlv4g.B3QnSuu1JoF2ecQURNhaahl4PyLP-s0e5bkHtZM4Slsg.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(progresses, speeds):
    answer = []

    time = 0
    count = 0

    while len(progresses) > 0:
        if (progresses[0] + (time*speeds[0])) >= 100:
            count+=1
            progresses.pop(0)
            speeds.pop(0)
        else:
            if count > 0:
                answer.append(count)
                count = 0
            time+=1

    answer.append(count)
    return answer
```



