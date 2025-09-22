# **소수찾기 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/42840?gad_source=1&gad_campaignid=22366107751&gbraid=0AAAAAC_c4nBshc-CwWVR4ap_1-k6WUxM5&gclid=CjwKCAjwxfjGBhAUEiwAKWPwDjqrJBvML2rRpKXzvayzTz7WRbdVSHgag0OiaZsiUgTy63_FLsko7xoCW0gQAvD_BwE

## **내 풀이**

### 첫번째 풀이

1. **HashSet** 을 이용하여 각 수포자들의 정답 갯수 구하기
1. **stream** 을 이용하여 max 값을 구한뒤, max 값의 집합을 구해 int 배열로 변환

### **내 코드**

![img](https://postfiles.pstatic.net/MjAyNTEwMDJfNCAg/MDAxNzU5Mzk2NTY1MDQ0.mnNEWaKmoS9LTwBzoF8vv6g_4zm6e1zgP7_EjZApTF8g.5JL5VSdiXllHxBes8fhQJe_uY-s1o5svSP-89b9ztn0g.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    public static int[] p1 = {1, 2, 3, 4, 5};
    public static int[] p2 = {2, 1, 2, 3, 2, 4, 2, 5};
    public static int[] p3 = {3, 3, 1, 1, 2, 2, 4, 4, 5, 5};

    public static int[] solution(int[] answers){

        Map<Integer, Integer> countMap = new HashMap<>();

        for(int i=0; i<answers.length; i++){
            if(p1[i % answers.length] == answers[i]) countMap.put(1, countMap.getOrDefault(1, 0) + 1);
            if(p2[i % answers.length] == answers[i]) countMap.put(2, countMap.getOrDefault(2, 0) + 1);
            if(p3[i % answers.length] == answers[i]) countMap.put(3, countMap.getOrDefault(3, 0) + 1);
        }

        int maxValue = countMap.values().stream()
                .max(Integer::compare)
                .orElse(0);

        return countMap.entrySet().stream()
                .filter(e -> e.getValue() == maxValue)
                .mapToInt(Map.Entry::getKey)
                .toArray();
    }
}
```



