# 퇴사

https://www.acmicpc.net/problem/14501

## 내 풀이

* 역순으로 for 문 돌리기!
  * 1일부터 계산하게 되면 하루하루 일당을 더하고, 몇 일 더 상담해야 하는지 기억하고, 다른 상담일 데이터도 기억하고 ..... 
  * 쉽지 않음.
* N 일 상담 할 경우: (오늘 일당) + (T일 뒤 최대 일당)
* N 일 상담 안 할 경우: (내일 최대 일당)


![img](https://postfiles.pstatic.net/MjAyNTEwMTdfNjIg/MDAxNzYwNjg1NTQ1OTUz.n3JYBvFlMbSxFK2QKWl0bptvEjp-eoAxQDVce3SNJiQg.EPoAj10Wa_VjRHy6X4M9P8CKZcl1-uA4spcMfq6QrmAg.PNG/image.png?type=w773)

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[][] call = new int[n][2];

        for(int i=0; i<n; i++){
            call[i][0] = sc.nextInt();
            call[i][1] = sc.nextInt();
        }

        int[] dp = new int[n+1];

        for(int i=n-1; i>=0; i--){
            if(call[i][0] + i > n){
                dp[i] = dp[i+1];
            }else{
                dp[i] = Math.max(call[i][1] + dp[call[i][0] + i], dp[i+1]);
            }
        }
        System.out.println(dp[0]);

    }

}
```

