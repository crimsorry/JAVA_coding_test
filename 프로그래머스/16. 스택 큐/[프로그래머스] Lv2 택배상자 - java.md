# 택배상자

https://school.programmers.co.kr/learn/courses/30/lessons/131704

## 내 풀이

```java
import java.util.*;

class Solution {
    public int solution(int[] order) {
        int n = order.length;
        int idx = 0;         
        int current = 1;      // 메인 벨트 포인터

        Deque<Integer> sub = new ArrayDeque<>();

        while (current <= n) {
            // 메인에서 바로 실을 수 있으면
            if (order[idx] == current) {
                idx++;
                current++;
            }
            // 보조에서 꺼낼 수 있으면
            else if (!sub.isEmpty() && sub.peek() == order[idx]) {
                sub.pop();
                idx++;
            }
            // 둘 다 아니면 메인을 보조로 보냄
            else {
                sub.push(current);
                current++;
            }
        }

        // 메인 다 끝난 뒤, 보조에서 더 꺼낼 수 있는지
        while (!sub.isEmpty() && idx < n && sub.peek() == order[idx]) {
            sub.pop();
            idx++;
        }

        return idx;
    }
}

```



