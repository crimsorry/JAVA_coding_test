# 이친수

https://www.acmicpc.net/problem/2193

## 내 풀이

* 처음에 int 타입으로 dp 이차원 배열을 선언하여 오버플로우가 일어남...!
* long 타입으로 변환하니 성공!


```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        long[][] dp = new long[n+1][2];
        dp[1][0] = 0;
        dp[1][1] = 1;

        for(int i=2; i<n+1; i++){
            dp[i][0] = dp[i-1][0] + dp[i-1][1];
            dp[i][1] += dp[i-1][0];
        }

        System.out.println(dp[n][0] + dp[n][1]);


    }

}

```

