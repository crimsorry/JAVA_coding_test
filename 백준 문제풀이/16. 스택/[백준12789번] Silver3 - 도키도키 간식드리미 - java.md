## 도키도키 간식드리미

https://www.acmicpc.net/problem/12789

## 내 풀이

* **stack** 의 개념에 대해 생각하기

햇갈린 점!

1. 줄서있는 곳 > 줄서는 공간으로 **한번만** 이동 가능

2. 줄서는 공간에서 순번대로 있는 경우 **while 반복**을 돌려 꺼내야 한다!

   > 이 점 고려가 안되서 왜 계속 틀린건지 고려함....
   >
   > ```
   > else if(!stack.isEmpty()){
   > 	int s = stack.pollFirst();
   >     if(s == now){
   >     	now++;
   >     }else{
   >         stack.offerFirst(su);
   > ```
   >
   > 이 코드처럼 최초 한번만 고려해서 틀렸다고 나왔음...

![img](https://postfiles.pstatic.net/MjAyNTEwMTlfMTU4/MDAxNzYwODY5MjQzNjQ4.KwTQl8TONXcNNji1zc5iUTusaAa5fjPBT77yZJq2AsEg.X3tQGgb6yJ7W66ToLIqTLwYODDcnnEc0G3zrPjubcx4g.PNG/image.png?type=w773)

```java
import java.util.ArrayDeque;
import java.util.Deque;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        Deque<Integer> stack = new ArrayDeque<>();
        int now = 1;

        for(int i=0; i<n; i++){
            stack.offerFirst(sc.nextInt());
            while(!stack.isEmpty()){
                int s = stack.peekFirst();
                if(s == now){
                    now++;
                    stack.pollFirst();
                }else{
                    break;
                }
            }
        }

        while(!stack.isEmpty()){
            int su = stack.peekFirst();
            if(su == now){
                now++;
                stack.pollFirst();
            }else{
                break;
            }
        }

        if(!stack.isEmpty()){
            System.out.println("Sad");
        }else{
            System.out.println("Nice");
        }
    }
}
```
