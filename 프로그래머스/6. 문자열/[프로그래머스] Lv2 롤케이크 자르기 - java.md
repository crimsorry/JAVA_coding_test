# 롤케이크 자르기

https://school.programmers.co.kr/learn/courses/30/lessons/132265



## 내 풀이

```python
import java.util.*;

class Solution {
    public int solution(int[] topping) {
        int answer = 0;
        
        Set<Integer> left = new HashSet<>();
        Map<Integer, Integer> right = new HashMap<>();
        
        for(int top : topping){
            right.put(top, right.getOrDefault(top, 0) + 1);
        }
        
        for(int top : topping){
            left.add(top);
            right.put(top, right.get(top) - 1);
            if(right.get(top) == 0) right.remove(top);
            if(left.size() == right.size()) answer++;
        }
        
        return answer;
    }
}
```



