## 최소공배수

https://www.acmicpc.net/problem/1934

## 내 풀이


```java
import java.util.*;

public class Main {

    static int gcd(int a, int b){
        while(b != 0){
            int tmp = a % b;
            a = b;
            b = tmp;
        }
        return a;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int t = sc.nextInt();

        while(t-- > 0){
            int a = sc.nextInt();
            int b = sc.nextInt();

            int g = gcd(a, b);
            System.out.println((long)a * b / g);  // long 필수
        }
    }
}

```
