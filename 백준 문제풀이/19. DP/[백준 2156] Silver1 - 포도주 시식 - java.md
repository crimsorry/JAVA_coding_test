# 포도주 시식

https://www.acmicpc.net/problem/2156

## 내 풀이

* 포도주를 마시는 경우의 수
  * 내 포도주 마시지 않고 i-1 번째 포도주 마시기
  * 내 포도주 마시고         i-2 번째까지 마셨던 포도주들 마시기
  * 내 포도주 마시고         i-3 번째까지 마셨던 포두주들 마시기 + I-1번째 포도주 마사기



```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] podo = new int[n+1];

        for(int i=1; i<n+1; i++){
            podo[i] = sc.nextInt();
        }

        long[] dp = new long[n+1];
        dp[1] = podo[1];
        if(n>1){
            dp[2] = dp[1]+podo[2];
        }

        for(int i=3; i<n+1; i++){
            dp[i] = Math.max(
                            dp[i-1],
                        Math.max(
                            dp[i-2],
                            dp[i-3] + podo[i-1]
                            )
                                + podo[i]
                            )
                    ;
        }

        System.out.println(Arrays.stream(dp).max().getAsLong());

    }

}

```

