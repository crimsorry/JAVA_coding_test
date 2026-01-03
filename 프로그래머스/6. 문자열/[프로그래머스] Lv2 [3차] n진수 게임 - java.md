# [3차] n진수 게임

https://school.programmers.co.kr/learn/courses/30/lessons/17687

## 내 풀이

```python
import java.util.*;

class Solution {
    public String solution(int n, int t, int m, int p) {
        StringBuilder convert = new StringBuilder();
        StringBuilder answer = new StringBuilder();
        
        for(int i = 0; convert.length() <= t * m; i++){
            convert.append(Integer.toString(i, n));
        }
        
        for(int i = p - 1;  answer.length() < t; i += m){
            answer.append(convert.charAt(i));
        }
        
        return answer.toString().toUpperCase();
    }
}
```



