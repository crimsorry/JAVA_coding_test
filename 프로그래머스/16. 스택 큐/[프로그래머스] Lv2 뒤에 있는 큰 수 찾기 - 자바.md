# 뒤에 있는 큰 수 찾기

https://school.programmers.co.kr/learn/courses/30/lessons/154539

## **내 풀이**

```java
import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
        int n = numbers.length;
        int[] answer = new int[n];
        Deque<Integer> stack = new ArrayDeque<>();

        for (int i = n - 1; i >= 0; i--) {
            while (!stack.isEmpty() && stack.peek() <= numbers[i]) {
                stack.pop();
            }

            answer[i] = stack.isEmpty() ? -1 : stack.peek();

            stack.push(numbers[i]);
        }

        return answer;
    }
}
```

