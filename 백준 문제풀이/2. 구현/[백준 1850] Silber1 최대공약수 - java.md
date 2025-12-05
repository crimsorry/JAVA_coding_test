## 최대공약수

https://www.acmicpc.net/problem/1850

## 내 풀이

* 문제 잘 읽기! 
  * 최대공약수 문제만 읽고 풀었다가 정답이 틀려서 몇분 삽질함...
  * 최대공약수만큼 '1' 을 출력시키는 문제였음...!


```java
import java.util.Scanner;

public class Main {

    public static long gcd(long a, long b){
        while(b > 0){
            long tmp = a % b;
            a = b;
            b = tmp;
        }
        return a;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        StringBuilder sb  = new StringBuilder();

        long a = sc.nextLong();
        long b = sc.nextLong();
        long gcd = gcd(a, b);

        while(gcd-->0){
            sb.append(1);
        }

        System.out.println(sb);

    }

}

```
