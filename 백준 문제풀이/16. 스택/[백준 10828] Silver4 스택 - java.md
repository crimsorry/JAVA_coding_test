# 스택

https://www.acmicpc.net/problem/10828

## 내 풀이

* Deque 이용하기!


```java
import java.util.Deque;
import java.util.LinkedList;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        Deque<Integer> deque = new LinkedList<>();

        for(int i=0; i<n; i++){
            String order = sc.next();
            if(order.equals("push")){
                deque.offerFirst(sc.nextInt());
            }else if(order.equals("pop")){
                Integer su = deque.pollFirst();
                System.out.println(su == null ? -1 : su);
            }else if(order.equals("size")){
                System.out.println(deque.size());
            }else if(order.equals("empty")){
                System.out.println(deque.isEmpty() ? 1 : 0);
            }else if(order.equals("top")){
                Integer su = deque.peekFirst();
                System.out.println(su == null ? -1 : su);
            }
        }

    }

}

```
