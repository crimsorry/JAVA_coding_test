# 계단 오르기

https://www.acmicpc.net/problem/2579

## 내 풀이

* dp 를 이용한 풀이
* 3계단 연속이 불가능 함으로
  * 전전 칸에서 건너 뛰거나
  * 전칸(3계단 연속은 불가능 함으로 해당 전칸은 전전칸에서 온 칸) 에서 오는 경우


![img](https://postfiles.pstatic.net/MjAyNTEwMTZfMTE3/MDAxNzYwNjA1Mzc4MjQx.MW2by3KBq86WWPSC41ZVWaaUk50ibX9FUYdJV4PCct4g.u_chX1PJztjAJ_1KRYLheQjCaTv6P0bs0mxHCAw0a6gg.PNG/image.png?type=w773)

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] score = new int[n];

        for(int i=0; i<n; i++){
            score[i] = sc.nextInt();
        }

        int[] dp = new int[n];
        dp[0] = score[0];
        if(n>1) dp[1] = score[0] + score[1];
        if(n>2) dp[2] = Math.max(dp[0] + score[2], score[1] + score[2]);


        for(int i=3; i<n; i++){
            dp[i] = Math.max(dp[i-2] + score[i], dp[i-3] + score[i-1] + score[i]);
        }

        System.out.println(dp[n-1]);

    }
    
}
```

