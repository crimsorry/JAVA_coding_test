# 절대값 힙

https://www.acmicpc.net/problem/11286

## 내 풀이

* 우선순위 큐 활용!
* **람다 Comparator** 선언하여 우선순위 기준 정렬

![image-20251030203435665](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20251030203435665.png)

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        PriorityQueue<Integer> q = new PriorityQueue<>((a, b) -> {
            int absA = Math.abs(a);
            int absB = Math.abs(b);
            if(absA==absB) return a - b;
            else return absA - absB;
        });

        while(n-->0){
            int x = sc.nextInt();

            if(x == 0){
                Integer su = q.poll();
                if(su == null){
                    System.out.println(0);
                }else{
                    System.out.println(su);
                }
            }else{
                q.offer(x);
            }
        }

    }

}
```

