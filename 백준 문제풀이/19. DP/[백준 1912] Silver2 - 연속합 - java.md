# 연속합

https://www.acmicpc.net/problem/1912

## 내 풀이


![img](https://postfiles.pstatic.net/MjAyNTEwMjdfMjY4/MDAxNzYxNTY5MDIyNTY3.kD00I7quK6v1_Ha6G7XcKW9PED_w3KoSwGGVIJcDnjsg.dEqo3YDhuagdnyHhdJTgpn5bWxoJgOJFGbwPxC15T9Yg.PNG/image.png?type=w773)

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] dp = new int[n];
        dp[0] = sc.nextInt();

        for(int i=1; i<n; i++){
            int su = sc.nextInt();
            dp[i] = Math.max(su, su + dp[i-1]);
        }

        System.out.println(Arrays.stream(dp).max().getAsInt());
    }

}
```

