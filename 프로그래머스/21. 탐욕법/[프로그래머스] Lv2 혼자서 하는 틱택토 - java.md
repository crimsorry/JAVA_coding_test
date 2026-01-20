# 혼자서 하는 틱택토

https://school.programmers.co.kr/learn/courses/30/lessons/160585

## 내 풀이

```java
class Solution {

    public int solution(String[] board) {
        int oCount = 0;
        int xCount = 0;

        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                if (board[i].charAt(j) == 'O') oCount++;
                if (board[i].charAt(j) == 'X') xCount++;
            }
        }

        // 1. 개수 규칙
        if (xCount > oCount) return 0;
        if (oCount > xCount + 1) return 0;

        boolean oWin = isWin(board, 'O');
        boolean xWin = isWin(board, 'X');

        // 2. 동시에 승리 불가
        if (oWin && xWin) return 0;

        // 3. 승리자와 말 개수 관계
        if (oWin && oCount != xCount + 1) return 0;
        if (xWin && oCount != xCount) return 0;

        return 1;
    }

    private boolean isWin(String[] board, char c) {
        // 가로
        for (int i = 0; i < 3; i++) {
            if (board[i].charAt(0) == c &&
                board[i].charAt(1) == c &&
                board[i].charAt(2) == c) {
                return true;
            }
        }

        // 세로
        for (int j = 0; j < 3; j++) {
            if (board[0].charAt(j) == c &&
                board[1].charAt(j) == c &&
                board[2].charAt(j) == c) {
                return true;
            }
        }

        // 대각선
        if (board[0].charAt(0) == c &&
            board[1].charAt(1) == c &&
            board[2].charAt(2) == c) {
            return true;
        }

        if (board[0].charAt(2) == c &&
            board[1].charAt(1) == c &&
            board[2].charAt(0) == c) {
            return true;
        }

        return false;
    }
}
```

