

# **여행경로 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/43164

## **내 풀이**

### **문제 풀이 흐름**

* **DFS** 로 풀기
* why? 모든 경로를 탐색해야 하기때문에 최단 거리문제 X
* 모두 같은 거리임으로 queue 를 사용하게 되면 오히려 속도가 더 걸릴 것으로 예상.
* 내 예상이 맞는지 코드를 통해 확인해보자.



### **문제상황**

### **주요 포인트**

### **내 코드**

* DFS 풀이

![img](https://postfiles.pstatic.net/MjAyNTA5MjRfMjA3/MDAxNzU4NzAwNTkyNDM1.cdZR79VECCz5boJGzy92pf6_fX3PWMFJ6yUQGWZQJw4g.qeJ3ANaFj3lwgTjP38ETFgBSjVH3Uj99ML1eOQvFQLAg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    
    public static ArrayList<String> answer;

    public static String[] solution(String[][] tickets){
        ArrayList<String> routes = new ArrayList<String>();
        routes.add("ICN");
        dfs(tickets, new boolean[tickets.length], routes);
        return answer.toArray(new String[0]);
    }

    public static void dfs(String[][] tickets, boolean[] visited, ArrayList<String> routes){
        String route = routes.get(routes.size()-1);

        if(routes.size()-1 == tickets.length){
            if(answer == null){
                answer = new ArrayList<>(routes);
            }else{
                String r1 = String.join("", routes);
                String r2 = String.join("", answer);

                if(r1.compareTo(r2) <0){
//                    answer = routes; // 얕은 복사 (주소 값 복사됨)
                    answer = new ArrayList<>(routes); // 깊은 복사
                }
            }
        }

        for(int i=0; i<tickets.length; i++){
            if(tickets[i][0].equals(route) && !visited[i]){
                visited[i] = true;
                routes.add(tickets[i][1]);
                dfs(tickets, visited, routes);
                visited[i] = false;
                routes.remove(routes.size()-1);
            }
        }

    }
}
```

### 



### 