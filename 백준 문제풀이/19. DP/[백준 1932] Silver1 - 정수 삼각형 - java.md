# 정수 삼각형

https://www.acmicpc.net/problem/1932

## 내 풀이

* 직전 삼격형의 max 값 저장

![img](https://postfiles.pstatic.net/MjAyNTEwMjdfMjM4/MDAxNzYxNTcwMDMyODgz.W-pKPDbotQrONi8H9pA8AAud09WXtTScbyP8La54D30g.uxLJcm2A7Vn3UkfiIKYBnHRY87-lYrBdVf0Cs0qIs40g.PNG/image.png?type=w773)

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[][] dp = new int[n][n+2];
        dp[0][1] = sc.nextInt();

        for(int i=1; i<n; i++){
            for(int j=1; j<i+2; j++){
                int su = sc.nextInt();
                dp[i][j] = Math.max(su + dp[i-1][j-1], su + dp[i-1][j]);
            }
        }

        System.out.println(Arrays.stream(dp[n-1]).max().getAsInt());
        
    }
}

```

