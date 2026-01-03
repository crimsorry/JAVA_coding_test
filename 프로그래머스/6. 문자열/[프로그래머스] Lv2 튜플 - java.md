# 튜플

https://school.programmers.co.kr/learn/courses/30/lessons/64065



## 내 풀이

```python
import java.util.*;

class Solution {
    public int[] solution(String s) {
        s = s.substring(2, s.length() - 2);

        String[] sets = s.split("\\},\\{");

        Arrays.sort(sets, Comparator.comparingInt(String::length));

        List<Integer> result = new ArrayList<>();
        Set<Integer> used = new HashSet<>();

        for (String set : sets) {
            String[] nums = set.split(",");
            for (String num : nums) {
                int n = Integer.parseInt(num);
                if (!used.contains(n)) {
                    used.add(n);
                    result.add(n);
                }
            }
        }

        return result.stream().mapToInt(i -> i).toArray();
    }
}

```



