# 알파벳 갯수

https://www.acmicpc.net/problem/10808

## 내 풀이


```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String ward = sc.next();
        int[] alphabet = new int[26];

        for(int i=0; i<ward.length(); i++){
            alphabet[ward.charAt(i) - 'a']++;
        }

        for(int a : alphabet){
            System.out.print(a + " ");
        }

    }
}

```
