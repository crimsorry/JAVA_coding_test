## 호텔 대실

https://school.programmers.co.kr/learn/courses/30/lessons/155651

## 내 풀이

```java
import java.util.*;

class Solution {
    public int solution(String[][] book_time) {
        int[][] times = new int[book_time.length][2];

        for (int i = 0; i < book_time.length; i++) {
            times[i][0] = toMinute(book_time[i][0]);
            times[i][1] = toMinute(book_time[i][1]) + 10; // 청소
        }

        Arrays.sort(times, Comparator.comparingInt(a -> a[0]));

        PriorityQueue<Integer> pq = new PriorityQueue<>();

        for (int[] t : times) {
            if (!pq.isEmpty() && pq.peek() <= t[0]) {
                pq.poll(); 
            }
            pq.offer(t[1]);
        }

        return pq.size();
    }

    private int toMinute(String time) {
        String[] t = time.split(":");
        return Integer.parseInt(t[0]) * 60 + Integer.parseInt(t[1]);
    }

}
```

