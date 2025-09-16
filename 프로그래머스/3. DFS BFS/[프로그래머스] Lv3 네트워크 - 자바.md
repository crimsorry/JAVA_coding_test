# **네트워크 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/43162

## **내 풀이**

### **문제 풀이 흐름**

1. DFS 를 활용 (or bfs 를 활용하여 각 queue 마다 방문시키기. 내일 풀어보자)
2. BFS 활용



### **결과**

![img](https://postfiles.pstatic.net/MjAyNTA5MDJfMjE4/MDAxNzU2ODE1OTI0MzM2._PTRBBfrb6C8bn8w64bNKHfoA5IQk6VGnCbozTbEPGwg.pfg57zY9F_P5JaWGIMb2kU57TwhtxCGa1HDaJGCJrPkg.PNG/image.png?type=w773)

### **내 코드**

```java
public class p43162 {

    public static void dfs(int[][] computers, int chk, boolean[] visited){
        visited[chk] = true;

        for(int j=0; j<computers.length; j++){
            if(chk!=j && computers[chk][j]!=1 && !visited[j]){
                dfs(computers, j, visited);
            }
        }
    }

    public static int solution(int n, int[][] computers) {
        int answer = 0;
        boolean[] visited = new boolean[computers.length];

        for(int i=0; i<computers.length; i++){
            if(!visited[i]){
                dfs(computers, i, visited);
                answer++;
            }
        }
        return answer;
    }

    public static void main(String[] args) {

        int n = 3;
        int[][] couputers = {{1, 1, 0}, {1, 1, 0}, {0, 0, 1}};

        System.out.println(solution(n, couputers));

    }

}
```

```java
import java.util.*;

class Solution {
    public int solution(int n, int[][] computers) {
        
        int answer = 0;
        boolean[] visited = new boolean[computers.length];

        for (int i = 0; i < computers.length; i++) {
            if (!visited[i]) {
                bfs(computers, i, visited);
                answer++;
            }
        }
        return answer;
    }
    
    public static void bfs(int[][] computers, int start, boolean[] visited) {
        Queue<Integer> queue = new LinkedList<>();
        queue.offer(start);
        visited[start] = true;

        while (!queue.isEmpty()) {
            int cur = queue.poll();

            for (int j = 0; j < computers.length; j++) {
                if (cur != j && computers[cur][j] == 1 && !visited[j]) {
                    visited[j] = true;
                    queue.offer(j);
                }
            }
        }
    }
    
   
}
```

