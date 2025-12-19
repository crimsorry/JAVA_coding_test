

# 실패율

https://school.programmers.co.kr/learn/courses/30/lessons/42889?language=java

## 내 풀이

```python
import java.util.*;

class Solution {
    public int[] solution(int N, int[] stages) {

        int[] stageCount = new int[N + 2]; 
        for (int s : stages) {
            stageCount[s]++;
        }

        int people = stages.length; 
        Map<Integer, Double> fail = new HashMap<>();

        for (int i = 1; i <= N; i++) {
            if (people == 0) {
                fail.put(i, 0.0);
            } else {
                fail.put(i, (double) stageCount[i] / people);
            }
            people -= stageCount[i];
        }

        List<Integer> list = new ArrayList<>(fail.keySet());

        list.sort((a, b) -> {
            if (fail.get(a).equals(fail.get(b))) {
                return a - b;
            }
            return Double.compare(fail.get(b), fail.get(a));
        });

        return list.stream().mapToInt(i -> i).toArray();
    }
}

```



