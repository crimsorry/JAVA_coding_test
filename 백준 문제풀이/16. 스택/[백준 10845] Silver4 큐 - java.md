# 큐

https://www.acmicpc.net/problem/10845

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
        Deque<Integer> q = new LinkedList<>();
        while(n-->0){
            String order = sc.next();
            if(order.equals("push")){
                q.offerLast(sc.nextInt());
            }else if(order.equals("pop")){
                Integer su = q.pollFirst();
                System.out.println(su == null ? -1 : su);
            }else if(order.equals("size")){
                System.out.println(q.size());
            }else if(order.equals("empty")){
                System.out.println(q.isEmpty() ? 1 : 0);
            }else if(order.equals("front")){
                Integer su = q.peekFirst();
                System.out.println(su == null ? -1 : su);
            }else if(order.equals("back")){
                Integer su = q.peekLast();
                System.out.println(su == null ? -1 : su);
            }
        }
    }

}

```
