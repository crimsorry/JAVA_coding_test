# 숫자 변환하기

https://school.programmers.co.kr/learn/courses/30/lessons/154538

## **내 풀이**

```java
import java.util.*;

class Solution {
    public int solution(int x, int y, int n) {
        boolean[] visited = new boolean[y + 1];
        Queue<int[]> q = new ArrayDeque<>();

        q.offer(new int[]{x, 0});
        visited[x] = true;

        while (!q.isEmpty()) {
            int[] cur = q.poll();
            int value = cur[0];
            int cnt = cur[1];

            if (value == y) return cnt;

            int[] nexts = {
                value + n,
                value * 2,
                value * 3
            };

            for (int next : nexts) {
                if (next <= y && !visited[next]) {
                    visited[next] = true;
                    q.offer(new int[]{next, cnt + 1});
                }
            }
        }

        return -1;
    }
}
```
