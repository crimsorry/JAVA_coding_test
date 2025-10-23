# 1, 2, 3 더하기

https://www.acmicpc.net/problem/9095

## 내 풀이

* 1, 2, 3, 4 ... 인 경우 직전 숫자들의 합과 같다는 원리 이용!


![img](https://postfiles.pstatic.net/MjAyNTEwMjdfMTMg/MDAxNzYxNTY3OTc4Nzgw.9YaaZBp74eoslVQUajdDy5dl6y4CmZedzKY9IvoVA0Qg.e3q-l6fBhLFkKmjXqXzHKWyJ2Je4DZhch2wWwD1yWi4g.PNG/image.png?type=w773)

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();
        int[] dp = new int[12];
        dp[1] = 1;
        dp[2] = 2;
        dp[3] = 4;

        for(int i=4; i<12; i++){
            dp[i] = dp[i-1] + dp[i-2] + dp[i-3];
        }

        while(t-->0){
            int n = sc.nextInt();
            System.out.println(dp[n]);
        }

    }

}
```

