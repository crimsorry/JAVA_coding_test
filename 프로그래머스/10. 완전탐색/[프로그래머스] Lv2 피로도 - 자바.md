## [프로그래머스] 피로도

https://school.programmers.co.kr/learn/courses/30/lessons/87946?gad_source=1&gad_campaignid=22366107751&gbraid=0AAAAAC_c4nCuvoL1uCl5_UpGjqGK9x-BO&gclid=CjwKCAjw6P3GBhBVEiwAJPjmLnN1ZesPRgOocXQ8xCm2Xn9uI6H5cecJAUyUCC1_qkjhjIufitRUCBoCuhgQAvD_BwE

## 첫번째 풀이
* static, public 등의 접근 제어 방식을 유념하며 코딩하기.
  * static: 메모리 상 처음부터 끝까지 필요한 경우에 사용.
  * 자바에서 배열 선언 시 특정 공간에 저장되어 지역변수로 사용 시 번지를 가져오게 된다.

![img](https://postfiles.pstatic.net/MjAyNTEwMDNfMjc4/MDAxNzU5NDk4MTIzNDE0.gwZ3ddL7xWhNqkKBjY0FwuEDsVyzAIQgH2JFc1BQEk4g.HY8z5qfr26P_q_yavwF47Ql9ZmI6buWfk7m_hWkKDNog.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
     boolean[] check;
     Stack<Point> st;
     int load = 0;
    
    public class Point{
        private int healthy;
        private int waste;
        
        public Point(int healthy, int waste){
            this.healthy = healthy;
            this.waste = waste;
        }
    }
    
    public int solution(int k, int[][] dungeons) {
        st = new Stack<>();
        check = new boolean[dungeons.length];
        // 반복
        dfs(k, dungeons.length, dungeons);
        
        return load;
    }
    
    public void dfs(int k, int n, int[][] dungeons){
        // 탈출
        if(st.size() == n){
            int inLoad = 0;
			for(Point i : st){
                if(k>=i.healthy) {
                    k = k-i.waste;
                    inLoad++;
                }
			}
            if(inLoad>load) load = inLoad;
			return;
		}
        
        for(int i=0; i<n; i++){
            if(!check[i]){
                check[i] = true;
                st.push(new Point(dungeons[i][0], dungeons[i][1]));
                dfs(k, n, dungeons);
                st.pop();
                check[i] = false;
            }
        }
    }
}
```

### 두번째 풀이

* **DFS** 를 이용한 풀이!
* **백트래킹**과 시간복잡도에 유념하여 코드 풀이

> 결과적으로 작년 풀이보다 성능 향상!!!

![img](https://postfiles.pstatic.net/MjAyNTEwMDNfNjAg/MDAxNzU5NDk4MDYwNzUw.exy9SQKkFUyDtEvCe_1fHFANFGVokgDdBxkniBfs2G0g.CRVj3quYJaAQL2mSvx5ln_eciULzw85Kcerj8DWiSx8g.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
     public static int solution(int k, int[][] dungeons){
        return dfs(k, dungeons, new boolean[dungeons.length], 0);
    }

    public static int dfs(int k, int[][] dungeons, boolean[] visited, int cnt){
        int max = cnt;

        for(int i=0; i<dungeons.length; i++){
            if(dungeons[i][0] <= k && !visited[i]){
                visited[i] = true;
                max = Math.max(max, dfs(k-dungeons[i][1], dungeons, visited, cnt+1));
                visited[i] = false;
            }
        }

        return max;
    }
}
```

