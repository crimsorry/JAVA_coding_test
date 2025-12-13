# 연속된 부분 수열의 합

https://school.programmers.co.kr/learn/courses/30/lessons/178870

## 내 풀이

```python
import java.util.*;

class Solution {
    public int[] solution(int[] sequence, int k) {
        int left = 0, right = 0;
        int sum = sequence[0];
        int minLen = Integer.MAX_VALUE;
        int[] answer = {0, 0};

        while (left <= right && right < sequence.length) {
            if (sum == k) {
                if (right - left < minLen) {
                    minLen = right - left;
                    answer[0] = left;
                    answer[1] = right;
                }
                sum -= sequence[left];
                left++;
            } else if (sum < k) {
                right++;
                if (right < sequence.length) {
                    sum += sequence[right];
                }
            } else { // sum > k
                sum -= sequence[left];
                left++;
            }
        }

        return answer;
    }
}

```



