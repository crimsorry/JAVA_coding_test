# **타겟 넘버 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/340198?language=java

## **내 풀이**

### **문제 풀이 흐름**

1. 가장 큰 정사각형 찾기(Largest Square in Matrix)



### **결과**

![img](https://postfiles.pstatic.net/MjAyNTA5MDRfMjQ2/MDAxNzU2OTgzMjE5MzI3.NqbzAvaqi3Z9-tBJtJzFb_h53EpMgWhKXcnFMd9b6WYg.pJhGBEWvuk9o5ayUdVe_M0AikdNeEdV9P-FkWeCRpJgg.PNG/image.png?type=w773)

### **내 코드**

```java
public class Solution {
    public int solution(int[] mats, String[][] park) {
        int r = park.length;
        int c = park[0].length;

        int[][] dp = new int[r][c];
        int maxSquare = 0;

        for (int i = 0; i < r; i++) {
            for (int j = 0; j < c; j++) {
                if ("-1".equals(park[i][j])) {
                    if (i == 0 || j == 0) {
                        dp[i][j] = 1;
                    } else {
                        dp[i][j] = 1 + Math.min(dp[i - 1][j],
                                        Math.min(dp[i][j - 1], dp[i - 1][j - 1]));
                    }
                    if (dp[i][j] > maxSquare) maxSquare = dp[i][j];
                } else {
                    dp[i][j] = 0;
                }
            }
        }

        int ans = -1;
        for (int m : mats) {
            if (m <= maxSquare && m > ans) ans = m;
        }
        return ans == -1 ? -1 : ans;
    }
}
```

### 