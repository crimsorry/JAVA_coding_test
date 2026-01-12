# 광물캐기

https://school.programmers.co.kr/learn/courses/30/lessons/172927

```java
import java.util.*;

class Solution {
    public int solution(int[] picks, String[] minerals) {

        int totalPicks = picks[0] + picks[1] + picks[2];
        int maxMine = Math.min(minerals.length, totalPicks * 5);

        List<int[]> chunks = new ArrayList<>();
        for (int i = 0; i < maxMine; i += 5) {
            int dia = 0, iron = 0, stone = 0;
            for (int j = i; j < i + 5 && j < maxMine; j++) {
                String m = minerals[j];
                if ("diamond".equals(m)) dia++;
                else if ("iron".equals(m)) iron++;
                else stone++;
            }
            chunks.add(new int[]{dia, iron, stone});
        }

        // 가장 공수가 많이 드는 집합 순으로 정렬
        chunks.sort((a, b) -> {
            int costA = a[0] * 25 + a[1] * 5 + a[2];
            int costB = b[0] * 25 + b[1] * 5 + b[2];
            return costB - costA;
        });

        int answer = 0;

        for (int[] c : chunks) {
            if (picks[0] > 0) {             
                answer += c[0] + c[1] + c[2];
                picks[0]--;
            } else if (picks[1] > 0) {     
                answer += c[0] * 5 + c[1] + c[2];
                picks[1]--;
            } else if (picks[2] > 0) {      
                answer += c[0] * 25 + c[1] * 5 + c[2];
                picks[2]--;
            } else break;
        }

        return answer;
    }
}

```

