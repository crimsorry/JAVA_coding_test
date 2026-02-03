# 보석쇼핑

https://school.programmers.co.kr/learn/courses/30/lessons/131127

## 내 풀이

```python
import java.util.*;

class Solution {
    public int solution(String[] want, int[] number, String[] discount) {
        Map<String, Integer> target = new HashMap<>();
        for (int i = 0; i < want.length; i++) {
            target.put(want[i], number[i]);
        }

        Map<String, Integer> map = new HashMap<>();
        int answer = 0;

        for (int i = 0; i < 10; i++) {
            map.put(discount[i], map.getOrDefault(discount[i], 0) + 1);
        }

        if (map.equals(target)) answer++;

        for (int i = 10; i < discount.length; i++) {
            String remove = discount[i - 10];
            map.put(remove, map.get(remove) - 1);
            if (map.get(remove) == 0) {
                map.remove(remove);
            }

            String add = discount[i];
            map.put(add, map.getOrDefault(add, 0) + 1);

            if (map.equals(target)) answer++;
        }

        return answer;
    }
}

```



