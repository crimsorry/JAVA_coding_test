# **메뉴 **리뉴얼

https://school.programmers.co.kr/learn/courses/30/lessons/72411

## **내 풀이**

```java
import java.util.*;

class Solution {
    
    Map<String, Integer> map = new HashMap<>();
    
    public String[] solution(String[] orders, int[] course) {
        
        for (String order : orders) {
            char[] chars = order.toCharArray();
            Arrays.sort(chars);
            
            for (int len : course) {
                if (chars.length >= len) {
                    combine(chars, 0, len, new StringBuilder());
                }
            }
        }
        
        List<String> result = new ArrayList<>();
        
        for (int len : course) {
            int max = 0;
            
            // 길이별 최대값 찾기
            for (String key : map.keySet()) {
                if (key.length() == len && map.get(key) >= 2) {
                    max = Math.max(max, map.get(key));
                }
            }
            
            if (max < 2) continue;
            
            for (String key : map.keySet()) {
                if (key.length() == len && map.get(key) == max) {
                    result.add(key);
                }
            }
        }
        
        Collections.sort(result);
        
        return result.toArray(new String[0]);
    }
    
    private void combine(char[] arr, int start, int len, StringBuilder sb) {
        if (sb.length() == len) {
            map.put(sb.toString(), map.getOrDefault(sb.toString(), 0) + 1);
            return;
        }
        
        for (int i = start; i < arr.length; i++) {
            sb.append(arr[i]);
            combine(arr, i + 1, len, sb);
            sb.deleteCharAt(sb.length() - 1);
        }
    }
}

```
