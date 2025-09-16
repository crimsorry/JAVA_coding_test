# 붕대감기 - 파이썬

https://school.programmers.co.kr/learn/courses/30/lessons/250137



## 내 풀이

#### 문제 풀이 흐름

1. attacks 반복문을 순회하며 피해량 만큼 체력을 깍는다.
2. 다음 공격 턴 전까지 체력을 회복한다. heal_time
3. t 초 이상 회복하게 된다면 y 만큼 추가로 회복한다.
4. 회복량이 최대 체력을 초과하면 최대체력으로 변경한다.
5. 순회한다.



#### 문제상황

* 예외처리 간과..
  * 회복된 체력이 최대 체력보다 큰 경우 최대체력으로 갱신해야한다.
  * 체력이 0 이하가 된 경우 break 해야 한다
  * 힐링이 한번 발동된 경우 아래의 경우가 아닌 이상 지속한다. 
    * 몬스트가 공격함
    * 최대 체력까지 회복함



#### 주요 포인트

`health if health > 0 else -1` : if 문을 한줄로 작성하는 방법



#### 결과

![img](https://postfiles.pstatic.net/MjAyNDEyMjNfMTg2/MDAxNzM0ODg2NzU2NDIy.xT2gAwC9N9lp0VfJgA3vUDbITKGZJltkCdUlbb74Il0g.bWAP_MCkb8yNgjKi_YxxMdH_ete0f1wqOUbFLJ3zcK8g.PNG/image.png?type=w773)



#### 내 코드

```python
def solution(bandage, health, attacks):
    max_health = health
    for i in range(0, len(attacks)):
        health -= attacks[i][1]
        if health <= 0:
            break
        if i < len(attacks) - 1:
            heal_time = attacks[i+1][0] - attacks[i][0] - 1
            a, b = divmod(heal_time, bandage[0])
            if heal_time > 0:
                if heal_time >= bandage[0]:
                    health +=  a * (bandage[0] * bandage[1] + bandage[2]) + b * bandage[1]
                else:
                    health += heal_time * bandage[1]
                health = min(health, max_health)
    
    return health if health > 0 else -1
```



