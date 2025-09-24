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

