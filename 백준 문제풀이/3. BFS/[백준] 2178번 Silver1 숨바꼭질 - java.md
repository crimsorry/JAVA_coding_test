# 숨바꼭질

https://www.acmicpc.net/problem/1697

## 내 답안

* visited 배열을 int 로 선언하여 각 순번을 기억시키기!!!

![Image](https://private-user-images.githubusercontent.com/31988854/509536809-dcfc6135-bf3f-444b-a1f4-21a3cff86c9c.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjIyNjE1NzQsIm5iZiI6MTc2MjI2MTI3NCwicGF0aCI6Ii8zMTk4ODg1NC81MDk1MzY4MDktZGNmYzYxMzUtYmYzZi00NDRiLWExZjQtMjFhM2NmZjg2YzljLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTExMDQlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUxMTA0VDEzMDExNFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTBkNGY5ZTEzYzM1YmFjMzUyNzRmMmFlZjEwZjVkOTUxODZjMGY1MGM4ZmU3ZTM4OTQ3NzNlODc2MzU5MWYxMWImWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.I0Jlfjd1WVqyBPClobgkfhO0tkEC_YDVWUxlzGwzC9I)

```java
import java.util.*;

public class Main {

    private static int n;
    private static int k;
    private static int[] visited = new int[100001];

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();
        k = sc.nextInt();

        System.out.println(bfs());
    }

    public static int bfs(){
        Queue<Integer> q = new LinkedList<>();
        q.add(n);
        visited[n] = 1;

        while(!q.isEmpty()){
            int x = q.poll();

            if(x == k) return visited[x] - 1;

            for(int i=0; i<3; i++){
                int y = 0;
                if(i==0){
                    y = x + 1;
                }else if(i==1){
                    y = x - 1;
                }else if(i==2){
                    y = x * 2;
                }
                if(y >= 0 && y < 100001 && visited[y] == 0){
                    visited[y] = visited[x] + 1;
                    q.add(y);
                }
            }
        }
        return -1;
    }

}
```

