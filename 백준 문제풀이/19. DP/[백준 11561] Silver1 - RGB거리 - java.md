# RGB 거리

https://www.acmicpc.net/problem/1149

## 내 풀이

![image-20251016183010752](C:\Users\xinex\AppData\Roaming\Typora\typora-user-images\image-20251016183010752.png)

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[][] color = new int[n][3];

        for(int i=0; i<n; i++){
            color[i][0] = sc.nextInt();
            color[i][1] = sc.nextInt();
            color[i][2] = sc.nextInt();
        }

        int[][] dp = new int[n][3];
        dp[0][0] = color[0][0];
        dp[0][1] = color[0][1];
        dp[0][2] = color[0][2];

        for(int i=1; i<n; i++){
            dp[i][0] = Math.min(dp[i-1][1] + color[i][0], dp[i-1][2] + color[i][0]);
            dp[i][1] = Math.min(dp[i-1][0] + color[i][1], dp[i-1][2] + color[i][1]);
            dp[i][2] = Math.min(dp[i-1][0] + color[i][2], dp[i-1][1] + color[i][2]);
        }
        
        System.out.println(Math.min(Math.min(dp[n-1][0], dp[n-1][1]), dp[n-1][2]));

    }

}
```

