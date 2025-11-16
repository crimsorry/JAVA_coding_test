# 가장 긴 감소하는 부분 수열

https://www.acmicpc.net/problem/11722

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
            dp[i] = 1;
            for(int j=0; j<n; j++){
                if(su[i] < su[j]){
                    dp[i] = Math.max(dp[i], dp[j]+1);
                }
            }
        }

        System.out.println(Arrays.stream(dp).max().getAsInt());

    }

}

```

