# 제곱수의 합

https://www.acmicpc.net/problem/1699

## 내 풀이

* 최악의 경우로 초기화 : dp[i] = i
  
* 각 제곱수의 최소 길이 구하기
  
  ```
  12 = 13 - 1*1
  9  = 13 - 2*2
  4  = 13 - 3*3
  ```
  


```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] dp = new int[n+1];

        for(int i=1; i<n+1; i++){
            dp[i] = i;
            for(int j=1; j*j<i+1; j++){
                dp[i] = Math.min(dp[i], dp[i - j*j] + 1);
            }
        }

        System.out.println(dp[n]);

    }
}

```

