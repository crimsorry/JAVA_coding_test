# 토마토

https://www.acmicpc.net/problem/7576

## 내 답안

* visited 를 통한 방문처리 X
  * tomato[node.x][node.y 조건으로 방문 처리 가능!


![Image](https://private-user-images.githubusercontent.com/31988854/508954454-57ed0f4b-997d-4283-a5ff-08d41b3a0531.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjIxNzUzNDcsIm5iZiI6MTc2MjE3NTA0NywicGF0aCI6Ii8zMTk4ODg1NC81MDg5NTQ0NTQtNTdlZDBmNGItOTk3ZC00MjgzLWE1ZmYtMDhkNDFiM2EwNTMxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTExMDMlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUxMTAzVDEzMDQwN1omWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTc0Y2E2ZWZkMjRmZTIyMmI5N2Y1MGYxZDYzMzljYWNhNTRiNDBjZDIwY2E2ZTRlZWI5NmM3MDU0NmJhZjE4ZTcmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.LSB07Fa72O6Clt2I-cOT6-etn5kv_l265DVWk3sZqeo)

```java
import java.util.*;

public class Main {

    private static int m;
    private static int n;
    private static int[][] tomato;
    private static int[] dx = {0, 1, 0, -1};
    private static int[] dy = {1, 0, -1, 0};

    public static class Node{
        int x;
        int y;

        Node(int x, int y){
            this.x = x;
            this.y = y;
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int answer = 0;
        m = sc.nextInt();
        n = sc.nextInt();
        tomato = new int[n][m];

        Queue<Node> q = new LinkedList<>();

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                tomato[i][j] = sc.nextInt();
                if(tomato[i][j] == 1){
                    q.add(new Node(i, j));
                }
            }
        }

        bfs(q);

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                if(tomato[i][j] == 0){
                    System.out.println(-1);
                    return;
                }else{
                    answer = Math.max(answer, tomato[i][j]);
                }
            }
        }

        System.out.println(answer-1);
    }

    public static void bfs(Queue<Node> q){
        while(!q.isEmpty()){
            Node node = q.poll();

            for(int i=0; i<4; i++){
                int nx = node.x + dx[i];
                int ny = node.y + dy[i];

                if(nx>=0 && nx<n && ny>=0 && ny<m){
                    if(tomato[nx][ny]==0 && tomato[node.x][node.y]>0){
                        tomato[nx][ny] = tomato[node.x][node.y] + 1;
                        q.add(new Node(nx, ny));
                    }
                }
            }
        }
    }

}
```

