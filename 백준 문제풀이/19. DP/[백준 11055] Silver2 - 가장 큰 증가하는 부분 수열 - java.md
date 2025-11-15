# 가장 큰 증가하는 부분 수열

https://www.acmicpc.net/problem/11055

## 내 풀이

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] su = new int[n];
        for(int i=0; i<n; i++){
            su[i] = sc.nextInt();
        }

        int[] dp = new int[n];

        for(int i=0; i<n; i++){
            dp[i] = su[i];
            for(int j=0; j<n; j++){
                if(su[i] > su[j]){
                    dp[i] = Math.max(dp[i], dp[j] + su[i]);
                }
            }
        }

        System.out.println(Arrays.stream(dp).max().getAsInt());

    }

}
```

