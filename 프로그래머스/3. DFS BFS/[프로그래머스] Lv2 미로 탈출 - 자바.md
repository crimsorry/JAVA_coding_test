# 미로탈출

https://school.programmers.co.kr/learn/courses/30/lessons/159993

## **내 풀이**

* BFS 최단거리를 이용한 문제
* visited 를 통한 방문처리로 속도 up
* Node class 를 통한 time 주소 값 가져오기

```java
import java.util.*;

class Solution {
    
    private static int width = 0;
    private static int height = 0;
    private final static int[] x = {1, 0, -1, 0};
    private final static int[] y = {0, 1, 0, -1};
    
    public static class Node{
        int cx;
        int cy;
        int time;
        
        public Node(int cx, int cy, int time){
            this.cx = cx;
            this.cy = cy;
            this.time = time;
        }
    }
    
    private Node lever(String[] maps){
        Queue<Node> q = new ArrayDeque<>();
        boolean[][] visited = new boolean[height][width];
        
        for(int i=0; i<height; i++){
            for(int j=0; j<width; j++){
                if(maps[i].charAt(j) == 'S'){
                    q.offer(new Node(i, j, 0));
                    visited[i][j] = true;
                    break;
                }
            }
            if(q.size()>0) break;
        }
        
        while(q.size()>0){
            Node node = q.poll();
            
            for(int i=0; i<4; i++){
                int dx = node.cx + x[i];
                int dy = node.cy + y[i];
                if(dx >=0 && dx < height && dy >=0 && dy < width){
                    char wall = maps[dx].charAt(dy);
                    if(!visited[dx][dy]){
                        if(wall == 'O' || wall == 'E'){
                            visited[dx][dy] = true;
                            q.offer(new Node(dx, dy, node.time+1));
                        }else if(wall == 'L'){
                            visited[dx][dy] = true;
                            return new Node(dx, dy, node.time+1);
                        }
                    }
                }
            }
        }
        return new Node(0, 0, -1);
    }
    
    private Node exit(String[] exitMap, Node leverNode){
        Queue<Node> q = new ArrayDeque<>();
        boolean[][] visited = new boolean[height][width];
        
        q.offer(leverNode);
        visited[leverNode.cx][leverNode.cy] = true;
        
        while(q.size()>0){
            Node node = q.poll();
            
            for(int i=0; i<4; i++){
                int dx = node.cx + x[i];
                int dy = node.cy + y[i];
                if(dx >=0 && dx < height && dy >=0 && dy < width){
                    char wall = exitMap[dx].charAt(dy);
                    if(!visited[dx][dy]){
                        if(wall == 'O' || wall == 'S'){
                            visited[dx][dy] = true;
                            q.offer(new Node(dx, dy, node.time+1));
                        }else if(wall == 'E'){
                            visited[dx][dy] = true;
                            return new Node(dx, dy, node.time+1);
                        }
                    }
                }
            }
        }
        return new Node(0, 0, -1);
    }
    
    public int solution(String[] maps) {
        int answer = 0;
        width = maps[0].length();
        height = maps.length;
        
        Node leverNode = lever(maps);
        
        answer = leverNode.time;
        
        if(answer < 0){
            return answer;
        }
        
        answer = exit(maps, leverNode).time;
        
        return answer;
    }
}
```

### DFS 풀이

* 시간초과

* 해당 문제는 최단거리 문제이므로 (문제에도 나와있음) 백트래킹 사용 시 모든 경로를 탐색하게 되어 최악의 시간복잡도가 나오게 됨.

* `O(4^(n*m))`

  ![img](https://postfiles.pstatic.net/MjAyNTA5MjNfMjc1/MDAxNzU4NjEwMDIyNjc3.iJzcHUQ9oNyDr-FedPXyQColA54d4qjjjA8HTRwtfhUg.o2IcjhHtmkBEJ-uQqoSehmXadrCuf-Yhz-CQvrUYr_8g.PNG/image.png?type=w773)

```java
package programmers;

public class P_1844 {

    private static int n;
    private static int m;
    private static int[] distanceX = {0, 1, 0, -1};
    private static int[] distanceY = {1, 0, -1, 0};
    private static int answer;

    public static class Node {
        private int x;
        private int y;

        public Node(int x, int y){
            this.x = x;
            this.y = y;
        }
    }

    public static int solution(int[][] maps){
        answer = -1;
        n = maps.length;
        m = maps[n-1].length;

        dfs(maps, new Node(0, 0), 1);
        return answer;
    }

    // dfs 풀자 호율성에서 0 점..!(시간초과) 정확점은 100점...
    public static void dfs(int[][] maps, Node node, int chk){
        if(node.x == n-1 && node.y == m-1) {
            if(answer != -1) {
                answer = Math.min(answer, chk);
            }else{
                answer = chk;
            }
        }else{
            for(int i=0; i<4; i++){
                int goX = node.x + distanceX[i];
                int goY = node.y + distanceY[i];
                if(goX >= 0 && goY >= 0 && goX < n && goY < m && maps[goX][goY] == 1){
                    maps[node.x][node.y] = 0;
                    dfs(maps, new Node(goX, goY), chk+1);
                    maps[node.x][node.y] = 1; // 백트래킹..! 다시 돌아올 수 있게!!
                }
            }
        }
    }
```

### BFS 풀이

* 층별로 Queue 에 노드를 넣어 최단 거리 탐색하기!

* **먼저 들어온 queue 는 가장 최단 거리로 들어온 node** 이므로 두번째, 세번째 들어온 node 보다 거리가 짧을 수 없음!

  * 따라서 방문처리 시키고 빽트래킹 하지 않아도 된다.

    `if(maps[goX][goY) == 1 && !visited[goX][goY]){`

    ​	`visited[goX][goY] = true;` 방문처리!

    ```
     1  #  9 10 11
     2  #  8  # 12
     3  #  7  8  9
     4  5  6  # 10
     #  #  #  # 11
    ```

    

![img](https://postfiles.pstatic.net/MjAyNTA5MjNfOTgg/MDAxNzU4NjExOTIxMjIx.Bn6-BiNHrEXGzwq8ZzTiC_FQsj4IILksd7hUb_-0LKMg.1FKh3FqjRhLe2U3oVJ2TmceuBtH0OswSz4tJkJ6YLoIg.PNG/image.png?type=w773)

```java
package programmers;

import java.util.LinkedList;
import java.util.Queue;

public class P_1844 {

    private static int n;
    private static int m;
    private static int[] distanceX = {0, 1, 0, -1};
    private static int[] distanceY = {1, 0, -1, 0};
    private static int answer;

    public static class NodeB {
        private int x;
        private int y;
        private int distance;

        public NodeB(int x, int y, int distance){
            this.x = x;
            this.y = y;
            this.distance = distance;
        }
    }

    public static int solution(int[][] maps){
        answer = -1;
        n = maps.length;
        m = maps[n-1].length;

        return bfs(maps);
    }

    // bfs: 층별로 Queue 에 노드를 넣어서 최단 거리 탐색하기
    public static int bfs(int[][] maps){
        Queue<NodeB> queue = new LinkedList<NodeB>();
        queue.offer(new NodeB(0, 0, 1));
        boolean[][] visited = new boolean[n][m];
        visited[0][0] = true;

        while(!queue.isEmpty()){
            NodeB nodeB = queue.poll();

            if(nodeB.x == n-1 && nodeB.y == m-1){
                return nodeB.distance;
            }

            for(int i=0; i<4; i++){
                int goX = nodeB.x + distanceX[i];
                int goY = nodeB.y + distanceY[i];
                if(goX >=0 && goY >=0 && goX < n && goY < m ){
                    if(maps[goX][goY] == 1 && !visited[goX][goY]){
                        visited[goX][goY] = true; // 최단거리를 위해 백트래킹 X
                        queue.offer(new NodeB(goX, goY, nodeB.distance+1));
                    }
                }
            }
        }
        return -1;
    }
    public static void main(String[] args) {
//        int[][] maps = {{1,0,1,1,1},{1,0,1,0,1},{1,0,1,1,1},{1,1,1,0,1},{0,0,0,0,1}};
        int[][] maps = {{1,0,1,1,1},{1,0,1,0,1},{1,0,1,1,1},{1,1,1,0,0},{0,0,0,0,1}};

        System.out.println(solution(maps));
    }

}

```

