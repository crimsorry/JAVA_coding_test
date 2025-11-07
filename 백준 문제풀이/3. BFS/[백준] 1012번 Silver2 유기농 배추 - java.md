# 유기농 배추

https://www.acmicpc.net/problem/1012

## 내 답안

* BFS
  * **Queue** 이용 하여 최소 탐색
  * **visited** 를 활용하여 모든 경우의 수를 탐색하기!

```java
import java.util.*;

public class Main {

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

        int t = sc.nextInt();

        while(t-->0){
            int m = sc.nextInt();
            int n = sc.nextInt();
            int k = sc.nextInt();
            int[][] baechu = new int[n][m];
            boolean[][] visited = new boolean[n][m];
            int answer = 0;

            for(int i=0; i<k; i++){
                int x = sc.nextInt();
                int y = sc.nextInt();
                baechu[y][x] = 1;
            }

            for(int i=0; i<n; i++){
                for(int j=0; j<m; j++){
                    if(baechu[i][j] == 1 && !visited[i][j]){
                        bfs(baechu, visited, i, j, m, n);
                        answer++;
                    }
                }
            }

            System.out.println(answer);
        }

    }

    public static void bfs(int[][] baechu, boolean[][] visited, int x, int y, int m, int n){
        Queue<Node> q = new LinkedList<>();
        q.add(new Node(x, y));

        while(!q.isEmpty()){
            Node node = q.poll();

            for(int i=0; i<4; i++){
                int nx = node.x + dx[i];
                int ny = node.y + dy[i];

                if(nx>=0 && nx<n && ny>=0 && ny<m){
                    if(!visited[nx][ny] && baechu[node.x][node.y] == 1 && baechu[nx][ny] == 1){
                        visited[nx][ny] = true;
                        q.add(new Node(nx, ny));
                    }
                }
            }
        }
    }

}
```

