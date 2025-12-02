## 요세푸스 문제

https://www.acmicpc.net/problem/1158

## 내 풀이

* Queue 사용!


```java
package baekjoon;

import java.util.*;

public class P_1158 {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        StringBuilder sb = new StringBuilder();

        int n = sc.nextInt();
        int k = sc.nextInt();
        Queue<Integer> q = new LinkedList<>();
        ArrayList<Integer> arr = new ArrayList<>();

        for(int i=1; i<n+1; i++){
            q.offer(i);
        }

        int cnt = 1;

        while(!q.isEmpty()){
            int su = q.poll();
            if(cnt < k){
                q.offer(su);
                cnt++;
            }else{
                arr.add(su);
                cnt = 1;
            }
        }

        sb.append("<");

        for(int i=0; i<n; i++){
            sb.append(arr.get(i));
            if(i<n-1){
                sb.append(", ");
            }
        }

        sb.append(">");

        System.out.println(sb);

    }

}

```
