# 서버 증설 횟수

https://school.programmers.co.kr/learn/courses/30/lessons/389479

## **내 풀이**

```java
import java.util.*;

class Solution {
    public int solution(int[] players, int m, int k) {
        int answer = 0;

        int n = players.length;
        int[] added = new int[n]; 
        int currentServers = 0;

        for (int i = 0; i < n; i++) {

            if (i >= k) {
                currentServers -= added[i - k];
            }

            int needServers = players[i] / m;

            if (currentServers < needServers) {
                int add = needServers - currentServers;
                added[i] = add;
                currentServers += add;
                answer += add;
            }
        }

        return answer;
    }
}
```

