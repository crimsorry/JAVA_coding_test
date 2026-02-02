# 쿼드 압축 후 개수 세기

https://school.programmers.co.kr/learn/courses/30/lessons/68936

## **내 풀이**

```java
class Solution {

    int zero = 0;
    int one = 0;

    public int[] solution(int[][] arr) {
        dfs(arr, 0, 0, arr.length);
        return new int[]{zero, one};
    }

    private void dfs(int[][] arr, int x, int y, int size) {
        int first = arr[x][y];
        boolean same = true;

        for (int i = x; i < x + size; i++) {
            for (int j = y; j < y + size; j++) {
                if (arr[i][j] != first) {
                    same = false;
                    break;
                }
            }
            if (!same) break;
        }

        if (same) {
            if (first == 0) zero++;
            else one++;
            return;
        }

        int half = size / 2;
        dfs(arr, x, y, half);                 // 좌상
        dfs(arr, x, y + half, half);          // 우상
        dfs(arr, x + half, y, half);          // 좌하
        dfs(arr, x + half, y + half, half);   // 우하
    }
}
```
