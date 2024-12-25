# 어린왕자 - 파이썬

https://www.acmicpc.net/problem/1004



## 내 풀이

#### 문제 풀이 흐름

1. 반복문을 t 만큼 돌린다. i
2. 출발점과 도착점을 변수로 선언한다. x1, y1, x2, y2
3. 반복문을 n 만큼 돌린다. j
4. 행성계의 중점과 반지름을 변수로 선언한다. cx, cy, r
5. count 변수를 선언한다
6. 입력된 행성의 지름이 출발점 보다 크고, 도착점보다 크다면 count + 1



#### 문제상황

* x 좌표가 같은경우 출발지에 포함안되고, 도착지에는 원이 포함됨
* 출발지에 포함안되고, 도착지에는 원이 포함됨
* 출발지에 원이 포함되고, 도착지에는 포함 안됨

> 위와 같이 경우의 수로 문제를 작성한 결과 20% 까지만 문제가 성공하다가 "틀렸습니다" 라는 결과가 나왔다. 무언가 빠진 경우의 수가 있다는 뜻.. 
>
> 따라서 제곱근을 이용한 거리의 사이값을 구하는 방식으로 풀이를 변경하였다.



#### 주요 포인트

* 행성계가 출발점 내부, 도착점 외부인 경우
* 행성계가 출발점 외부, 도착점 내부인 경우

**출발점 과 행성계 중앙 사이의 거리** = `(x1−cx)2+(y1−cy)2`

**도착점 과 행성계 중앙 사이의 거리** = `(x2−cx)2+(y2−cy)2`

**출발점만 원 내부에 있는 경우 또는 도착점만 원 내부에 있는 경우**



#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMjVfOTEg/MDAxNzM1MTM0MjkwMTA3.3NbQV4mleijP5at7rz9LQlaTSkfA6Rl4kIwxEzRwrTcg.fYwFGrJxuQX7tl5klJ-UYojx32fLLAl6I6Tsjg3RMPsg.PNG/image.png?type=w773)



#### 내 코드

```python
t = int(input())

for i in range(t):
    count = 0
    x1, y1, x2, y2 = map(int, input().split())
    n = int(input())
    for j in range(n):
        cx, cy, r = map(int, input().split())

        # 출발점과 행성계 중심 사이 거리
        dist1 = (x1 - cx) ** 2 + (y1 - cy) ** 2
        # 도착점과 행성계 중심 사이 거리
        dist2 = (x2 - cx) ** 2 + (y2 - cy) ** 2
        # 반지름 제곱
        r_squared = r ** 2

        # 출발점만 원 내부에 있는 경우 또는 도착점만 원 내부에 있는 경우
        if (dist1 < r_squared < dist2) or (dist1 > r_squared > dist2):
            count += 1
    print(count)
```



#### 잘못된 풀이

```python
t = int(input())

for i in range(t):
    count = 0
    x1, y1, x2, y2 = map(int, input().split())
    n = int(input())
    for j in range(n):
        cx, cy, r = map(int, input().split())
        if x1 == x2: # x 좌표가 같은경우
            if cy+r > y2 and cy - r > y1: # 출발지에 포함안되고, 도착지에는 원이 포함됨
                count+=1
        elif cx+r > x2 and cx-r > x1: # 출발지에 포함안되고, 도착지에는 원이 포함됨
            count+=1
        elif cx-r < x1 < cx+r < x2: # 출발지에 원이 포함되고, 도착지에는 포함 안되는 경우
            count+=1
    print(count)
```

