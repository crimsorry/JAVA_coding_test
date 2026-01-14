# 과일 장수

https://school.programmers.co.kr/learn/courses/30/lessons/135808

```python
import java.util.*;

class Solution {
    public int solution(int k, int m, int[] score) {
        Arrays.sort(score);
        int result = 0;
        int n = score.length;

        for (int i = n - m; i >= 0; i -= m) {
            result += score[i] * m;
        }

        return result;
    }
}

```

