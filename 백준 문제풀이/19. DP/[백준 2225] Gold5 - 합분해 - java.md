# 2Xn 타일링 2

https://www.acmicpc.net/problem/11727

## 내 풀이

* 점화식 경우 생각하기!
  * i-1 : 세로 한줄 추가 => *1
  * i-2 : 가로 2줄 추가 & 네모 박스 한개 추가 => *2

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] dp = new int[n];
        dp[0] = 1;
        if(n>1) dp[1] = 3;

        for(int i=2; i<n; i++){
            dp[i] = (dp[i-1] + 2*(dp[i-2])) % 10007;
        }

        System.out.println(dp[n-1]);

    }

}
```

