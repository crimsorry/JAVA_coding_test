# 미로 탐색

https://www.acmicpc.net/problem/2178

## 내 답안

* BFS
  * **Queue** 이용 하여 최소 탐색
  * 재귀 XXXX

```java
import java.util.*;

public class Main {

    private static int n;
    private static int m;
    private static int[][] maze;
    private static boolean[][] visited;
    private static int[] dx = {0, 1, 0, -1};
    private static int[] dy = {1, 0, -1, 0};

    public static class Node{
        int x;
        int y;

        public Node(int x, int y){
            this.x = x;
            this.y = y;
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();
        m = sc.nextInt();
        maze = new int[n][m];
        visited = new boolean[n][m];

        for(int i=0; i<n; i++){
            String line = sc.next();
            for(int j=0; j<m; j++){
                maze[i][j] = line.charAt(j) - '0';
            }
        }

        Queue<Node> q = new LinkedList<>();
        visited[0][0] = true;
        q.add(new Node(0, 0));

        bfs(q);

        System.out.println(maze[n-1][m-1]);

    }


    public static void bfs(Queue<Node> q){
        while(!q.isEmpty()){
            Node node = q.poll();

            for(int i=0; i<4; i++){
                int nx = node.x + dx[i];
                int ny = node.y + dy[i];

                if(nx>=0 && nx<n && ny>=0 && ny<m){
                    if(!visited[nx][ny] && maze[nx][ny]==1){
                        maze[nx][ny] = maze[node.x][node.y] + 1;
                        visited[nx][ny] = true;
                        q.add(new Node(nx, ny));
                    }
                }
            }
        }
    }

}

```

