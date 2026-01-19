# 리코쳇 로봇

https://school.programmers.co.kr/learn/courses/30/lessons/169199?language=java

## **내 풀이**

```java
import java.util.*;

class Solution {

    static class Node {
        int r, c, cnt;
        Node(int r, int c, int cnt) {
            this.r = r;
            this.c = c;
            this.cnt = cnt;
        }
    }

    public int solution(String[] board) {
        int n = board.length;
        int m = board[0].length();

        char[][] map = new char[n][m];
        boolean[][] visited = new boolean[n][m];

        int sr = 0, sc = 0;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                map[i][j] = board[i].charAt(j);
                if (map[i][j] == 'R') {
                    sr = i;
                    sc = j;
                }
            }
        }

        int[] dr = {1, -1, 0, 0};
        int[] dc = {0, 0, 1, -1};

        Queue<Node> q = new LinkedList<>();
        q.offer(new Node(sr, sc, 0));
        visited[sr][sc] = true;

        while (!q.isEmpty()) {
            Node cur = q.poll();

            if (map[cur.r][cur.c] == 'G') {
                return cur.cnt;
            }

            for (int d = 0; d < 4; d++) {
                int nr = cur.r;
                int nc = cur.c;

                while (true) {
                    int tr = nr + dr[d];
                    int tc = nc + dc[d];

                    if (tr < 0 || tr >= n || tc < 0 || tc >= m || map[tr][tc] == 'D') {
                        break;
                    }
                    nr = tr;
                    nc = tc;
                }

                if (!visited[nr][nc]) {
                    visited[nr][nc] = true;
                    q.offer(new Node(nr, nc, cur.cnt + 1));
                }
            }
        }

        return -1;
    }
}

```
