# 최댓값과 최솟값

https://school.programmers.co.kr/learn/courses/30/lessons/12939

## 내 풀이

```python
import java.util.*;

class Solution {
    public String solution(String s) {
        String answer = "";
        
        int[] arr = Arrays.stream(s.split(" "))
                          .mapToInt(Integer::parseInt)
                          .toArray();
        
        int max = Arrays.stream(arr).max().getAsInt();
        int min = Arrays.stream(arr).min().getAsInt();
        
        return min + " " + max;
    }
}
```



