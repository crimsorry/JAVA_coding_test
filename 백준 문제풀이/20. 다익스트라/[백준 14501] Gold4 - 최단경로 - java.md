# 최단경로

https://www.acmicpc.net/problem/1753

## 내 풀이

* **다익스트라** 알고리즘!
  * 그래프에서 시작점 > 다른 모든 정점까지의 최단 거리(최소비용)



https://postfiles.pstatic.net/MjAyNTEwMjBfNjgg/MDAxNzYwOTY0OTA5Nzgw.TJnpsCAC-fR32n9qbLTZtuuxwYnWg8B4GJZemYwK_c8g.fXovZOUUWTn1gyPmK4tHSGDzyL5Rsc3vUsqBTdFk6bQg.PNG/image.png?type=w773

```java
import java.io.*;
import java.util.*;

public class Main {
    static class Node implements Comparable<Node> {
        int vertex, weight;
        Node(int vertex, int weight) {
            this.vertex = vertex;
            this.weight = weight;
        }
        public int compareTo(Node o) {
            return this.weight - o.weight; // 거리 짧은 순
        }
    }

    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st = new StringTokenizer(br.readLine());

        int V = Integer.parseInt(st.nextToken()); // 정점 수
        int E = Integer.parseInt(st.nextToken()); // 간선 수
        int K = Integer.parseInt(br.readLine());  // 시작점

        List<List<Node>> graph = new ArrayList<>();
        for (int i = 0; i <= V; i++) graph.add(new ArrayList<>());

        for (int i = 0; i < E; i++) {
            st = new StringTokenizer(br.readLine());
            int u = Integer.parseInt(st.nextToken());
            int v = Integer.parseInt(st.nextToken());
            int w = Integer.parseInt(st.nextToken());
            graph.get(u).add(new Node(v, w));
        }

        int[] dist = new int[V + 1];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[K] = 0;

        PriorityQueue<Node> pq = new PriorityQueue<>();
        pq.offer(new Node(K, 0));

        while (!pq.isEmpty()) {
            Node now = pq.poll();

            if (now.weight > dist[now.vertex]) continue;

            for (Node next : graph.get(now.vertex)) {
                int newDist = dist[now.vertex] + next.weight;
                if (newDist < dist[next.vertex]) {
                    dist[next.vertex] = newDist;
                    pq.offer(new Node(next.vertex, newDist));
                }
            }
        }

        StringBuilder sb = new StringBuilder();
        for (int i = 1; i <= V; i++) {
            if (dist[i] == Integer.MAX_VALUE) sb.append("INF\n");
            else sb.append(dist[i]).append("\n");
        }
        System.out.print(sb);
    }
}

```

