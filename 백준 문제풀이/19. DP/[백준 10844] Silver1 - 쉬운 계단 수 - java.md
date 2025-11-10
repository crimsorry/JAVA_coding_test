# 쉬운 계단 수

https://www.acmicpc.net/problem/10844

## 내 풀이

* n=1
  * 1~9 >  계단 수 1

* n=2
  * 0 > 계단수 가능한 경우는 i-1 이 1
  * 1 > 계단수 가능한 경우는 i-1 이 0, 2
  * 2 > 계단수 가능한 경우는 i-1 이 1, 3
  * ...
  * 9 > 계단수 가능한 경우는 i-1 이 8


```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[][] dp = new int[n+1][10];
        for(int i=1; i<10; i++){
            dp[1][i] = 1;
        }

        for(int i=2; i<n+1; i++){
            for(int j=0; j<10; j++){
                if(j==0){
                    dp[i][j] = dp[i-1][j+1];
                }else if(j<9){
                    dp[i][j] = dp[i-1][j-1] + dp[i-1][j+1];
                }else if(j==9){
                    dp[i][j] = dp[i-1][j-1];
                }
            }
        }

        int answer = 0;

        for(int i=0; i<10; i++){
            answer = (answer + dp[n][i]) % 1000000000;
        }

        System.out.println(answer);

    }

}
```

