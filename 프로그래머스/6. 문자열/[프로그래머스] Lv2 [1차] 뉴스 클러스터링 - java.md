

# [1차] 뉴스 클러스터링

https://school.programmers.co.kr/learn/courses/30/lessons/17677

## 내 풀이

```python
import java.util.*;

class Solution {
    public int solution(String str1, String str2) {
        Map<String, Integer> m1 = buildMultiSet(str1);
        Map<String, Integer> m2 = buildMultiSet(str2);

        if (m1.isEmpty() && m2.isEmpty()) return 65536;

        int inter = 0;
        int union = 0;

        Set<String> keys = new HashSet<>();
        keys.addAll(m1.keySet());
        keys.addAll(m2.keySet());

        for (String k : keys) {
            int c1 = m1.getOrDefault(k, 0);
            int c2 = m2.getOrDefault(k, 0);
            inter += Math.min(c1, c2);
            union += Math.max(c1, c2);
        }

        return (int) Math.floor(((double) inter / union) * 65536);
    }

    private Map<String, Integer> buildMultiSet(String s) {
        s = s.toLowerCase(Locale.ROOT);
        Map<String, Integer> map = new HashMap<>();

        for (int i = 0; i < s.length() - 1; i++) {
            char a = s.charAt(i);
            char b = s.charAt(i + 1);

            if (isAlpha(a) && isAlpha(b)) {
                String token = "" + a + b;
                map.put(token, map.getOrDefault(token, 0) + 1);
            }
        }
        return map;
    }

    private boolean isAlpha(char c) {
        return c >= 'a' && c <= 'z';
    }
}

```



