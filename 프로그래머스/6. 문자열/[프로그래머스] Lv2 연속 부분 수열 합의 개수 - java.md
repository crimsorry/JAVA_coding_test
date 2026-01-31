# 연속 부분 수열 합의 개수

https://school.programmers.co.kr/learn/courses/30/lessons/131701



## 내 풀이

```java
import java.util.*;

class Solution {
    public int solution(int[] elements) {
        int n = elements.length;
        int[] extended = new int[n * 2];

        for (int i = 0; i < n; i++) {
            extended[i] = elements[i];
            extended[i + n] = elements[i];
        }

        int[] prefix = new int[n * 2 + 1];
        for (int i = 1; i <= n * 2; i++) {
            prefix[i] = prefix[i - 1] + extended[i - 1];
        }

        Set<Integer> set = new HashSet<>();

        for (int len = 1; len <= n; len++) {
            for (int start = 0; start < n; start++) {
                int sum = prefix[start + len] - prefix[start];
                set.add(sum);
            }
        }

        return set.size();
    }
}
```



