## 동전0

https://www.acmicpc.net/problem/11047

## 내 답안

![img](https://postfiles.pstatic.net/MjAyNTEwMjdfMTEy/MDAxNzYxNTcyNTYxNjA5.IZToyz-NPn7NWIA8yBvC778x7oxeXfJCnhcHU0oACmkg.mmJ_l4LL_vsd0u4OIw4CQQn6MHL5ymU2xGF2Y5_fBA4g.PNG/image.png?type=w773)

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int k = sc.nextInt();
        Integer[] coin = new Integer[n];
        int answer = 0;

        for(int i=0; i<n; i++){
            coin[i] = sc.nextInt();
        }

        Arrays.sort(coin);

        for(int i=n-1; i>=0; i--){
            if (coin[i] <= k) {
                answer += k / coin[i];
                k = k % coin[i];
            }
            if (k == 0) break;
        }

        System.out.println(answer);

    }

}
```



