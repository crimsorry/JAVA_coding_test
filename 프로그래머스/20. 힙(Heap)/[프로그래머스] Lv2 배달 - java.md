# 배달

https://school.programmers.co.kr/learn/courses/30/lessons/12978



## 내 풀이

```java
import java.util.*;

class Solution {
    
    static class Node {
        int village;
        int cost;
        
        Node(int village, int cost) {
            this.village = village;
            this.cost = cost;
        }
    }
    
    public int solution(int N, int[][] road, int K) {
        
        List<List<Node>> graph = new ArrayList<>();
        
        for (int i = 0; i <= N; i++) {
            graph.add(new ArrayList<>());
        }
        
        // 그래프 구성 (양방향)
        for (int[] r : road) {
            int a = r[0];
            int b = r[1];
            int c = r[2];
            
            graph.get(a).add(new Node(b, c));
            graph.get(b).add(new Node(a, c));
        }
        
        // 다익스트라
        int[] dist = new int[N + 1];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[1] = 0;
        
        PriorityQueue<Node> pq = new PriorityQueue<>(
            (o1, o2) -> o1.cost - o2.cost
        );
        
        pq.offer(new Node(1, 0));
        
        while (!pq.isEmpty()) {
            Node current = pq.poll();
            
            if (current.cost > dist[current.village]) continue;
            
            for (Node next : graph.get(current.village)) {
                int newCost = current.cost + next.cost;
                
                if (newCost < dist[next.village]) {
                    dist[next.village] = newCost;
                    pq.offer(new Node(next.village, newCost));
                }
            }
        }
        
        // K 이하 개수 카운트
        int answer = 0;
        for (int i = 1; i <= N; i++) {
            if (dist[i] <= K) {
                answer++;
            }
        }
        
        return answer;
    }
}

```



