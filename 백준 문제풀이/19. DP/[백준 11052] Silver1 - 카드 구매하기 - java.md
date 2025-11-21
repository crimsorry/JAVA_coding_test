# 카드 구매하기

https://www.acmicpc.net/problem/11052

## 내 풀이

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] card = new int[n+1];
        int[] dp = new int[n+1];

        for(int i=1; i<n+1; i++){
            card[i] = sc.nextInt();
        }

        for(int i=1; i<n+1; i++){
            for(int j=1; j<i+1; j++){
                dp[i] = Math.max(dp[i], dp[i-j] + card[j]);
            }
        }

        System.out.println(dp[n]);
        
    }

}

```

