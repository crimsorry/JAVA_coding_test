# 스티커

https://www.acmicpc.net/problem/9465

## 내 풀이

* 점화식을 이용한 풀이


```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while(t-->0){
            int n = sc.nextInt();
            int[][] sticker = new int[n][2];
            for(int i=0; i<2; i++){
                for(int j=0; j<n; j++){
                    sticker[j][i] = sc.nextInt();
                }
            }

            int[][] dp = new int[n][2];
            dp[0][0] = sticker[0][0];
            dp[0][1] = sticker[0][1];

            if(n>1){
                dp[1][0] = dp[0][1] + sticker[1][0];
                dp[1][1] = dp[0][0] + sticker[1][1];
            }

            for(int i=2; i<n; i++){
                dp[i][0] = Math.max(dp[i-2][1], dp[i-1][1]) + sticker[i][0];
                dp[i][1] = Math.max(dp[i-2][0], dp[i-1][0]) + sticker[i][1];
            }

            System.out.println(Math.max(dp[n-1][0], dp[n-1][1]));

        }

    }

}
```

