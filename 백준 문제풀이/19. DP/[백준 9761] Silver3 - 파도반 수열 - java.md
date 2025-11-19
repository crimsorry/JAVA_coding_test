# 파도반 수열

https://www.acmicpc.net/problem/9461

## 내 풀이

* 규칙성 찾아 점화식에 대입하기!
  


```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while(t-->0){
            int n = sc.nextInt();
            long[] dp = new long[n+1];
            dp[1] = 1;
            if(n>1) dp[2] = 1;

            for(int i=3; i<n+1; i++){
                dp[i] = dp[i-3] + dp[i-2];
            }

            System.out.println(dp[n]);

        }

    }

}
```

