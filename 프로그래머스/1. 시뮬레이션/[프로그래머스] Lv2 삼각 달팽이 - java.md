# 삼각 달팽이

https://school.programmers.co.kr/learn/courses/30/lessons/68645

## 내 풀이

```python
class Solution {
    public int[] solution(int n) {
        int[][] board = new int[n][n];
        int max = n * (n + 1) / 2;

        int x = -1, y = 0;
        int num = 1;

        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                if (i % 3 == 0) {         
                    x++;
                } else if (i % 3 == 1) {   
                    y++;
                } else {              
                    x--;
                    y--;
                }
                board[x][y] = num++;
            }
        }

        int[] answer = new int[max];
        int idx = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j <= i; j++) {
                answer[idx++] = board[i][j];
            }
        }
        return answer;
    }
}

```



