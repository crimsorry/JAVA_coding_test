# 징검다리

https://www.acmicpc.net/problem/11561

## 내 풀이

* 1 + 2 + 3 ... 합을 구하기 위해 **가우스 공식** 이용!
  * `N(N + 1) / 2`


![img](https://postfiles.pstatic.net/MjAyNTEwMTRfMjY0/MDAxNzYwNDQ3MzM5NjM5.8RM3scJJSpWsHIb8hh2MVARVXRwDv5ToHPbnuxvyFawg.NvBF48JzcOrGL80_JyqyWuKYeCE8L09B1YUzr8ci_UEg.PNG/image.png?type=w773)

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        for(int i=0; i<t; i++){
            long n = sc.nextLong();

            long left = 1;
            long right = (long) Math.sqrt(2 * n) + 1;
            long answer = 0;

            while(left <= right){
                long mid = (left + right) / 2;
                long sum = mid * (mid + 1) / 2;

                if(sum <= n){
                    left = mid + 1;
                    answer = mid;
                }else{
                    right = mid - 1;
                }
            }

            System.out.println(answer);
        }
    }

}
```

