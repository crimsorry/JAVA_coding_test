# **다리를 지나는 트럭- 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/42583?language=java

## **내 풀이**

### 첫번째 풀이

1. **큐**에 다리 길이 담기

### **내 코드**

![img](https://postfiles.pstatic.net/MjAyNTEwMDVfMzIg/MDAxNzU5NjcyNjM4NTE0.VAQBic_xxwtdigzmgA-zpAW6cOgWbhWvvcxPZVnmxewg.C3frK5Kckq3WM0b2EqZ5Emh2V-4Rezc0TiAr_Z0tICIg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    public static int solution(int bride_length, int weight, int[] truck_weights){

        Queue<Integer> q = new LinkedList<>();

        for(int i=0; i<bride_length; i++){
            q.offer(0);
        }

        int time = 0;
        int total_weights = 0;
        int idx = 0;
        while(!q.isEmpty()){
            total_weights-=q.poll(); // 앞 트럭 지나가기
            time++; // 시간 + 1

            if(idx < truck_weights.length){
                int truck = truck_weights[idx];

                if(truck + total_weights <= weight){
                    q.offer(truck);
                    total_weights+=truck;
                    idx++;
                }else{
                    q.offer(0);
                }
            }
        }

        return time;
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

