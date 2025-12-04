## 나머지

https://www.acmicpc.net/problem/10430

## 내 풀이


```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();
        int c = sc.nextInt();

        System.out.println((a+b)%c);
        System.out.println(((a%c) + (b%c)) % c);
        System.out.println((a*b) % c);
        System.out.println(((a%c) * (b%c)) % c);

    }

}

```
