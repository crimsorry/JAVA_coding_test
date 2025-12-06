## GCD 합

https://www.acmicpc.net/problem/9613

## 내 풀이


```java
package baekjoon;

import java.util.*;

public class P_9613 {

    public static long gcd(long a, long b){
        while(b>0){
            long tmp = a % b;
            a = b;
            b = tmp;
        }
        return a;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while(t-->0){
            int n = sc.nextInt();
            long answer = 0;
            Integer[] arr = new Integer[n];

            for(int i=0; i<n; i++){
                arr[i] = sc.nextInt();
            }

            Arrays.sort(arr);

            for(int i=0; i<n; i++){
                for(int j=i+1; j<n; j++){
                    answer += gcd(arr[i], arr[j]);
                }
            }

            System.out.println(answer);
        }

    }
}

```
