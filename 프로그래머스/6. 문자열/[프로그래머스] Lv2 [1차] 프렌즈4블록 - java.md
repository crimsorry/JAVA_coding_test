# [1차] 프렌즈 4블록

https://school.programmers.co.kr/learn/courses/30/lessons/17679



## 내 풀이

```java
class Solution {
    public int solution(int m, int n, String[] board) {
        char[][] map = new char[m][n];
        for (int i = 0; i < m; i++) {
            map[i] = board[i].toCharArray();
        }

        int answer = 0;

        while (true) {
            boolean[][] remove = new boolean[m][n];
            boolean found = false;

            for (int i = 0; i < m - 1; i++) {
                for (int j = 0; j < n - 1; j++) {
                    char c = map[i][j];
                    if (c == ' ') continue;

                    if (map[i][j + 1] == c &&
                        map[i + 1][j] == c &&
                        map[i + 1][j + 1] == c) {

                        remove[i][j] = true;
                        remove[i][j + 1] = true;
                        remove[i + 1][j] = true;
                        remove[i + 1][j + 1] = true;
                        found = true;
                    }
                }
            }

            if (!found) break;

            for (int i = 0; i < m; i++) {
                for (int j = 0; j < n; j++) {
                    if (remove[i][j]) {
                        map[i][j] = ' ';
                        answer++;
                    }
                }
            }

            for (int j = 0; j < n; j++) {
                int emptyRow = m - 1;
                for (int i = m - 1; i >= 0; i--) {
                    if (map[i][j] != ' ') {
                        map[emptyRow][j] = map[i][j];
                        if (emptyRow != i) map[i][j] = ' ';
                        emptyRow--;
                    }
                }
            }
        }

        return answer;
    }
}

```



