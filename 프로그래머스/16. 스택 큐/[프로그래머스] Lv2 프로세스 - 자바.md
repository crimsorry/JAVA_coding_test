# **소수찾기 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/42587

## **내 풀이**

### 첫번째 풀이

1. 프로세스 **큐**에 담기
1. 배열에 **정렬**된 우선순위 프로세스 넣기
1. 큐를 활용하여 location 실행 번지 수 찾기

### **내 코드**

![img](https://postfiles.pstatic.net/MjAyNTEwMDNfMTIx/MDAxNzU5NTAxNzYyODAy.Ot7hqMwV7szkTp5jLyrgkpXnrk-22MF4R5aBCKMOczUg.MUJfxhfdy-9axr0sxmL_axui_7cD2KnJiOZgPnZp-rkg.PNG/image.png?type=w773)

```java
import java.util.Arrays;
import java.util.LinkedList;
import java.util.Queue;

class Solution {
   public static int solution(int[] priorities, int location){
        int max = 0;
        int cnt = 0;

        Queue<Integer> q = new LinkedList<>();

        for(int i=0; i<priorities.length; i++){
            q.offer(priorities[i]);
        }

        int[] processes = Arrays.stream(priorities)
                                .sorted()
                                .toArray();
        max = processes[priorities.length-1];

        while(!q.isEmpty()){
            int process = q.poll();

            if(process == max){
                cnt++;
                if(location == 0) break;
                max = processes[processes.length-1-cnt];
            }else{
                q.offer(process);
            }
            location--;
            if(location<0) location = q.size()-1;
        }
        return cnt;
    }
    
}
```

### 두번째 풀이

* **우선순위 큐** 사용!

* Queue 에 {원 순번, 프로세스} 를 넣고, PriorityQueue 에 내림차순 프로세스 넣기!

  ![img](https://postfiles.pstatic.net/MjAyNTEwMDRfMTcx/MDAxNzU5NTA2Mzk3NjIw.VeBmU73lKcElU0YFp_qhZabAXtpkPoyV9ABApemu8ZMg.5dCImV99yK7lmnBHbD2i6yd0u2AtWmSTimhdFjXt2ygg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
   public static int solution(int[] priorities, int location){
        int cnt = 0;

        Queue<int[]> q = new LinkedList<>();
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());

        for(int i=0; i<priorities.length; i++){
            q.offer(new int[]{i, priorities[i]});
            pq.offer(priorities[i]);
        }

        while(!q.isEmpty()){
            int[] process = q.poll();
            int max = pq.poll();

            if(process[1] == max){
                cnt++;
                if(process[0] == location) break;
            }else{
                q.offer(process);
                pq.offer(max);
            }
        }
        return cnt;
    }
    
}
```

