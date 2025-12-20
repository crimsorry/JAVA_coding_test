# 유연근무제

https://school.programmers.co.kr/learn/courses/30/lessons/388351?language=java

## 내 풀이

```python
class Solution {
    public int solution(int[] schedules, int[][] timelogs, int startday) {
        int n = schedules.length;
        int answer = 0;

        for (int i = 0; i < n; i++) {
            int base = schedules[i];

            int h = base / 100;
            int m = base % 100 + 10;
            if (m >= 60) {
                h++;
                m -= 60;
            }
            int limit = h * 100 + m;

            boolean ok = true;

            for (int d = 0; d < 7; d++) {
                int day = (startday + d - 1) % 7 + 1;

                if (day == 6 || day == 7) continue;

                if (timelogs[i][d] > limit) {
                    ok = false;
                    break;
                }
            }

            if (ok) answer++;
        }

        return answer;
    }
}
```



