# 요격시스템

https://school.programmers.co.kr/learn/courses/30/lessons/181188?language=java

## 내 풀이

* 발사 끝 점인 e 를 기준으로 정렬하는 것이 key!

![img](https://postfiles.pstatic.net/MjAyNTEwMjJfMjgy/MDAxNzYxMTM4NTI0Njk5.XKXnvwLt9VOMeWbfEXghWsZ4VMqUgcuGM87uQ7sum3wg.-r_o32CpiJ0iWLxNEZnqx40qfx7txLHIwn1AGf8Z8mYg.PNG/image.png?type=w773)

```java
import java.util.Arrays;

class Solution {
    public int solution(int[][] targets) {
        int answer = 0;

        Arrays.sort(targets, (s, e) -> Integer.compare(s[1], e[1]));
        double end = -1;

        for(int i=0; i<targets.length; i++){
            int s = targets[i][0];
            int e = targets[i][1];
            
            if(end < s){
                end = e - 0.5;
                answer++;
            }
        }

        return answer;
    }
}
```

