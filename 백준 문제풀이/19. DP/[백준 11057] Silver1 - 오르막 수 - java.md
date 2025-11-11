# 오르막 수

https://www.acmicpc.net/problem/11057

## 내 풀이


```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[][] dp = new int[n+1][10];

        for(int i=0; i<10; i++){
            dp[1][i] = 1;
        }

        for(int i=2; i<n+1; i++){
            for(int j=0; j<10; j++){
                if (j == 0) dp[i][j] = dp[i-1][j];
                else dp[i][j] = (dp[i-1][j] + dp[i][j-1]) % 10007;
            }
        }

        int answer = 0;

        for(int i=0; i<10; i++){
            answer = (answer + dp[n][i]) % 10007;
        }

        System.out.println(answer);

    }

}

```

