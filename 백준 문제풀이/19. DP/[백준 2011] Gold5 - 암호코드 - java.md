# 암호코드

https://www.acmicpc.net/problem/2011

## 내 풀이

* 1자리 해석
* 2자리 해석
* 불가능한 경우!


```java
import java.util.*;

public class Main {

    static final int MOD = 1000000;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String s = sc.next();

        if(s.charAt(0) == '0'){
            System.out.println(0);
            return;
        }

        int n = s.length();
        int[] dp = new int[n+1];
        dp[0] = 1;
        dp[1] = 1;

        for(int i=2; i<=n; i++){
            char c1 = s.charAt(i-1);
            char c0 = s.charAt(i-2);

            if(c1 != '0'){
                dp[i] = (dp[i] + dp[i-1]) % MOD;
            }

            int num = (c0 - '0') * 10 + (c1 - '0');
            if(num >= 10 && num <= 26){
                dp[i] = (dp[i] + dp[i-2]) % MOD;
            }

            if(dp[i] == 0 && c1 == '0' && !(num == 10 || num == 20)){
                System.out.println(0);
                return;
            }
        }

        System.out.println(dp[n]);
    }

}

```

