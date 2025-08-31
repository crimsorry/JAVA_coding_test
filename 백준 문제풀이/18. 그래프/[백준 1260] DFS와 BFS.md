# **DFS와 BFS - 자바**

https://www.acmicpc.net/problem/1260

## **내 풀이**

### **주요 포인트**

**DFS**

- 깊이 우선 탐색
- **처음 방문하는 정점이 `재귀에 진입`할 때 마다**

**BFS**

- 넓이 우선 탐색
- `Queue` 를 이용하면 더 직관적!
- 탐색할 정점을 Queue 에 넣고
- **처음 방문하는 정점이 `큐에서 빠질때` 마다**

### **결과**

![img](https://postfiles.pstatic.net/MjAyNTA4MzFfMjg0/MDAxNzU2NjM1MDc1MDA2.XqkzdJj7MVDxd4JaZ1b_nBjqr96Hb9szneBDvRDaGcEg.ZaxWjz_NrHiwJ0PA6MXKF2R3li6YBP_z7fCXhJG_bmsg.PNG/image.png?type=w773)

### **내 코드**

```java
package baekjoon;

import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class baekjoon_1260 {

    static int n, m, v;
    static int[][] graph;
    static boolean[] visited;

    public static void dfs(int node) {
        System.out.print(node + " ");

        visited[node] = true;
        for(int i=1; i<=n; i++){
            if(graph[node][i] == 1 && !visited[i]){
                dfs(i);
            }
        }
    }

    public static void bfs(int node) {
        Queue<Integer> q = new LinkedList<>();
        q.add(node);
        visited[node] = true;
        while(!q.isEmpty()) {
            int now = q.poll();
            System.out.print(now + " ");
            for(int i = 1; i <= n; i++) {
                if(graph[now][i] == 1 && !visited[i]) {
                    q.offer(i);
                    visited[i] = true;
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();
        m = sc.nextInt();
        v = sc.nextInt();
        graph = new int[n + 1][n + 1];
        visited = new boolean[n + 1];

        for(int i=0; i<m; i++){
            int src = sc.nextInt();
            int dst = sc.nextInt();
            graph[src][dst] = 1;
            graph[dst][src] = 1;
        }

        dfs(v);
        System.out.println();
        visited = new boolean[n + 1];
        bfs(v);

    }

}

```

### 