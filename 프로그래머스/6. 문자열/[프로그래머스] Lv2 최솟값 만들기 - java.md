# 최솟값 만들기

https://school.programmers.co.kr/learn/courses/30/lessons/12941



## 내 풀이

```python
import java.util.*;

class Solution {
    public int solution(int[] A, int[] B) {
        Arrays.sort(A);
        Arrays.sort(B);

        int sum = 0;
        int n = A.length;

        for (int i = 0; i < n; i++) {
            sum += A[i] * B[n - 1 - i]; 
        }

        return sum;
    }
}

```



