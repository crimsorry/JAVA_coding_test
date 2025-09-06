# **타겟 넘버 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/1844

## **내 풀이**

### **문제 풀이 흐름**

1. **초기화**
   - 시작점 `(0,0)`을 큐에 넣고 BFS 탐색을 준비
   - `maps[x][y]` 값은 해당 칸까지의 최단 거리로 갱신
2. **BFS 탐색**
   - 큐에서 노드를 꺼내 네 방향(상하좌우)으로 이동을 시도
   - 이동할 수 있고(`== 1`) 아직 방문하지 않은 칸이면, 이전 칸의 값 + 1 로 갱신하고 큐에 추가
   - 이렇게 하면 각 칸에 도달할 때까지의 최단 거리가 저장
3. **도착지 확인**
   - 탐색이 끝난 뒤, `maps[n-1][m-1]` 값이 1보다 크면 도착까지의 최단 거리이므로 반환
   - 만약 여전히 1 이하라면 도착할 수 없다는 뜻이므로 `-1`을 반환



### **결과**

![img](https://postfiles.pstatic.net/MjAyNTA5MDVfMTcw/MDAxNzU3MDcyNTM4NjI0.jw8EagoAGkXRpUNfcYlY4_Tae4Xlb1FPJ-8GZnavGgAg.yyx5aqiXHB98adccPim6qX8kLG9LSvrg9WDyBczA8zog.PNG/image.png?type=w773)



### **내 코드**

```java
import java.util.*;

class Solution {
    static int[] nx = {0, 0, 1, -1};
	static int[] ny = {1, -1, 0, 0};
    
    public int solution(int[][] maps) {
        int n = maps.length;
    	int m = maps[0].length;
    	
    	Queue<Node> q = new LinkedList<Node>();
    	q.offer(new Node(0, 0));
    	
    	bfs(q, maps, n, m);
    	
    	if(maps[n-1][m-1] <= 1) return -1;
        return maps[n-1][m-1];
    }
    
     static class Node{
    	private int x;
    	private int y;
    	
    	public Node(int x, int y) {
    		this.x = x;
    		this.y = y;
    	}
    }
    
    public static void bfs(Queue<Node> q, int[][] maps, int n, int m) {
    	while(!q.isEmpty()) {
    		Node node = q.poll();
    		
    		for(int i=0; i<4; i++) {
    			if(node.x+nx[i] < 0 || node.y+ny[i] < 0 || node.x+nx[i] >= n || node.y+ny[i] >= m) continue;
    			if(maps[(node.x+nx[i])][(node.y+ny[i])] == 1) {
        			maps[node.x+nx[i]][node.y+ny[i]] = maps[node.x][node.y] + 1;
    				q.offer(new Node(node.x+nx[i], node.y+ny[i]));
    			}
    		}
    	}
    	
    	
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

