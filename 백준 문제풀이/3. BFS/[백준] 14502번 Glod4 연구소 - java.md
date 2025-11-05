# 연구소

https://www.acmicpc.net/problem/14502

## 내 답안

1. 벽 3개 세울 수 있는 경우 list
   * 깊은 복사 이용!
2. BFS > 바이러스가 퍼진 경우
3. 안전한 경우 구하기


![Image](https://private-user-images.githubusercontent.com/31988854/510141719-6f71e260-aea0-474d-b972-93e8c5e87313.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjIzNDkxNzksIm5iZiI6MTc2MjM0ODg3OSwicGF0aCI6Ii8zMTk4ODg1NC81MTAxNDE3MTktNmY3MWUyNjAtYWVhMC00NzRkLWI5NzItOTNlOGM1ZTg3MzEzLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTExMDUlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUxMTA1VDEzMjExOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTVmNWI1MmNjYTBmMmI1YjVlOWYyOTdiODgxZTNmYTA0Yjc3NDJiYjM3NWIyMGYwY2Q3MDM2MmE1NGVjMWZjOTgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.DORN7IFnypicOkBUbnzeFzwU81qFrkrcOFupJ-4hz-U)

```java
import java.util.*;

public class Main {

    private static int n;
    private static int m;
    private static List<Node> array = new ArrayList<>();
    private static List<Node> virus = new ArrayList<>();
    private static List<List<Node>> wall = new ArrayList<>();
    private static int[] dx = {0, 1, 0, -1};
    private static int[] dy = {1, 0, -1, 0};

    private static class Node{
        int x;
        int y;

        Node(int x, int y){
            this.x = x;
            this.y = y;
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();
        m = sc.nextInt();
        int[][] map = new int[n][m];

        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                map[i][j] = sc.nextInt();
                if(map[i][j] == 0) array.add(new Node(i, j));
                if(map[i][j] == 2) virus.add(new Node(i, j));
            }
        }

        int answer = 0;

        build(new ArrayList<>(), 0, 0);

        for(int i=0; i<wall.size(); i++){
            int[][] buildMap = new int[n][m];
            for (int x = 0; x < n; x++) {
                buildMap[x] = map[x].clone();
            }
            buildMap[wall.get(i).get(0).x][wall.get(i).get(0).y] = 1;
            buildMap[wall.get(i).get(1).x][wall.get(i).get(1).y] = 1;
            buildMap[wall.get(i).get(2).x][wall.get(i).get(2).y] = 1;

            Queue<Node> q = new LinkedList<>();
            for(int j=0; j<virus.size(); j++){
                q.offer(virus.get(j));
            }

            answer = Math.max(answer, bfs(q, buildMap));
        }

        System.out.println(answer);
    }

    // 빈칸 세우는 메소드
    public static void build(List<Node> list, int start, int depth){
        if(depth == 3){
            wall.add(new ArrayList<>(list));
            return;
        }

        for(int i=start; i<array.size(); i++){
            list.add(array.get(i));
            build(list, i+1, depth+1);
            list.remove(list.size()-1); // 마지막 요소 삭제
        }

    }

    public static int bfs(Queue<Node> q, int[][] map){
        while(!q.isEmpty()){
            Node node = q.poll();

            for(int i=0; i<4; i++){
                int nx = node.x + dx[i];
                int ny = node.y + dy[i];

                if(nx>=0 && nx<n && ny>=0 && ny<m){
                    if(map[nx][ny] == 0){
                        map[nx][ny] = 2;
                        q.add(new Node(nx, ny));
                    }
                }
            }
        }

        return getSafe(map);
    }

    public static int getSafe(int[][] map){
        int cnt = 0;
        for(int i=0; i<n; i++){
            for(int j=0; j<m; j++){
                if(map[i][j] == 0){
                    cnt++;
                }
            }
        }
        return cnt;
    }

}
```

