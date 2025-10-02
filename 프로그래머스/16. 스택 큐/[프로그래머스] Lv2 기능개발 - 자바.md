# **기능개발- 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/42586?language=java

## **내 풀이**

### 첫번째 풀이

1. 프로세스 **큐**에 담기
1. 모든 작업 하루치 진행
1. 배포할 수 있는 작업 묶음 세기

### **내 코드**

![img](https://postfiles.pstatic.net/MjAyNTEwMDRfMTU4/MDAxNzU5NTc2OTc3MTYy.Q0GgO9TGMH5cJO4zitxZ7v2pclVUoybdhXNrOO7142gg.rrCUtisIVCy0P9lQo3btBJohHIpiEKd0HcEKgrI9G98g.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    public static int[] solution(int[] progresses, int[] speeds){
        Queue<int[]> q = new LinkedList<>();
        ArrayList<Integer> answer = new ArrayList<>();
        
        for(int i=0; i<progresses.length; i++){
            q.offer(new int[]{i, progresses[i], 0});
        }

        int day = 0;
        while(!q.isEmpty()){
            int[] progress = q.peek();

            if(progress[1]<100){
                day++;
                // 모든 작업 하루치 진행
                for(int[] task : q){
                    task[1] += speeds[task[0]];
                }
                continue;
            }

            // 배포할 수 있는 작업 묶음 세기
            int count = 0;
            while(!q.isEmpty() && q.peek()[1] >= 100){
                q.poll();
                count++;
            }
            answer.add(count);
        }

        return answer.stream().mapToInt(i -> i).toArray();
    }
}
```

### 두번째 플이

* for 문을 이용한 풀이!

  ![img](https://postfiles.pstatic.net/MjAyNTEwMDRfODIg/MDAxNzU5NTc3MTMxNDc4.XfHQlkk08vewI-4Xyu4w7QCQterl9kfYMbWJ5DT9yP4g.GZ0LG5qSC1XExaLSxyo_vXBHouOcvFKCTFlwVNV0LK4g.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    public int[] solution(int[] progresses, int[] speeds) {
        List<Integer> result = new ArrayList<>();
        
        int n = progresses.length;
        int[] days = new int[n];
        
        for (int i = 0; i < n; i++) {
            days[i] = (int) Math.ceil((100.0 - progresses[i]) / speeds[i]);
        }
        
        int maxDay = days[0]; 
        int count = 1;     
        
        for (int i = 1; i < n; i++) {
            if (days[i] <= maxDay) {
                count++;
            } else {
                result.add(count);
                count = 1;
                maxDay = days[i];
            }
        }
        
        result.add(count);
        
        return result.stream().mapToInt(Integer::intValue).toArray();
    }
}
```

