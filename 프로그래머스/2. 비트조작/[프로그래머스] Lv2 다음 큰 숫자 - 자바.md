# 다음 큰 숫자

https://school.programmers.co.kr/learn/courses/30/lessons/12911

## **내 풀이**

```java
class Solution {
    public int solution(int n) {
        int targetCount = Integer.bitCount(n);
        int next = n + 1;

        while (true) {
            if (Integer.bitCount(next) == targetCount) {
                return next;
            }
            next++;
        }
    }
}

```

