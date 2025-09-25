# **N-Queen - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/12952

## **내 풀이**

### 첫번째 시도

1. DFS 를 이용한 풀이
1. 백트래킹을 이용하여 양옆, 위아래, 대각선을 true / false 로 만들기

하지만 시간 효율성과 예외처리 로직이 복잡하여 시도에 그치고 만 코드...

### **내 코드**

```java
package backjoon;

public class P_12952 {

    public static int solution(int n) {
        int answer = 0;
        if(dfs(n, new boolean[n][n], 0)) answer++;
        return answer;
    }

    public static boolean dfs(int n, boolean[][] visited, int chk){
        if(chk == n){
            return true;
        }
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                if(!visited[i][j]){
                    // 양옆, 위아래, 대각선 true 처리.
                    for(int k=0; k<n; k++){
                        for(int l=0; l<n; l++){
                            if(!visited[i][j]){
                                if(i==k && j!=l) visited[k][j] = true; // 양옆
                                if(i!=k && j==l) visited[k][j] = true; // 위아래
                                // 대각선
                            }
                        }
                    }
                    dfs(n, visited, chk+1);
                    // 백트래킹
                }
            }
        }
        return false;
    }

```

### 두번째 풀이

* true 처리할 영역을 각 배열로 선언!

  * 열 = 0, 1, 2, 3 ...
  * 좌상, 우하 대각선 = 0,0 1,1 2,2 ... row - col = 0 (모든 값이 0 이므로 구분을 위해  n - 1
  * 좌하, 우상 대각선 = 0,2 1,1 2,0 ... row + col = row * 2

  ![img](https://postfiles.pstatic.net/MjAyNTEwMDJfMjM4/MDAxNzU5NDEzNjc1Mjg4.09ICVxDARQc8ZKT0n4kG3ll_8SE4e87xKruSE3bcf_Eg.JiGIVNRnIJqtwqt8YtTq2fM--QBOMEbelROaYyCcNjsg.PNG/image.png?type=w773)

```java
class Solution {
    static int answer;
    static boolean[] digit1;
    static boolean[] digit2;
    static boolean[] digit3;

    public static int solution(int n) {
        answer = 0;
        digit1 = new boolean[n]; // 열 = 0, 1, 2, 3 ...
        digit2 = new boolean[2*n]; // 좌상, 우하 대각선 = 0,0 1,1 2,2 ... row - col = 0 (모든 값이 0 이므로 구분을 위해  n - 1
        digit3 = new boolean[2*n]; // 좌하, 우상 대각선 = 0,2 1,1 2,0 ... row + col = row * 2

        dfs(0, n);
        
        return answer;
    }

    public static void dfs(int row, int n){
        if(row == n){
            answer++;
            return;
        }

        for(int col=0; col<n; col++){
            if(digit1[col] || digit2[row - col + n - 1] || digit3[row + col]) continue;

            digit1[col] = digit2[row - col + n - 1] = digit3[row + col] = true;

            dfs(row+1, n);

            // 백트랙킹
            digit1[col] = digit2[row - col + n - 1] = digit3[row + col] = false; 
        }
    }
}
```

