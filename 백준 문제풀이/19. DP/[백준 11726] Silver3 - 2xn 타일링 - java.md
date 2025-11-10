# 2Xn 타일링

https://www.acmicpc.net/problem/11726

## 내 풀이

* dp 의 특성 기억하기!
  * 이전 번호 기억

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] dp = new int[n];
        dp[0] = 1;
        if (n > 1) dp[1] = 2; 

        for(int i=2; i<n; i++){
            dp[i] = (dp[i-1] + dp[i-2]) % 10007;
        }

        System.out.println(dp[n-1]);
    }

}

```

