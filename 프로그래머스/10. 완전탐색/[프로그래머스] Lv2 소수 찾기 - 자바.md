# **소수찾기 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/42839?language=java

## **내 풀이**

### **문제 풀이 흐름**

1. **DFS**  - 백트래킹을 이용하여 모든 경우의 수 구하기
2. **TreeSet** 에 값을 넣어 오름차순 정렬 만들기
3. 마지막 수를 이용해 **에라토스테네스의 체** 공식 사용!
4. 각 경우의 수가 소수인지 visited 배열을 통해 확인!

### **내 코드**

![img](https://postfiles.pstatic.net/MjAyNTEwMDFfNDQg/MDAxNzU5MzI2NDQ2NDAz.L5Hf64CnbywFpm5Nl137HbCvK6UuFHAP3rqVJEg7ZGsg.7QcSxDDJbtQxp1YjDdYIGIcaOpGEzG8QhmYVl1tNjPcg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    
    public static TreeSet<Integer> treeSet = new TreeSet<Integer>();

    public static int solution(String numbers){
        int cnt = 0;
        String[] nums = numbers.split("");

        dfs(nums, new boolean[nums.length+1], "");

        int last = treeSet.pollLast();
        boolean[] visited = sosu(last);

        for(Integer num : treeSet){
            if(!visited[num]) cnt++;
        }

        if(!visited[last]) cnt++;

        return cnt;
    }

    public static void dfs(String[] nums, boolean[] visited, String num){
        if(!num.isEmpty()){
            treeSet.add(Integer.parseInt(num));
        }

        for(int i=0; i<nums.length; i++){
            if(!visited[i]){
                visited[i] = true;
                dfs(nums, visited, num + nums[i]);
                visited[i] = false;
            }
        }
    }

    public static boolean[] sosu(Integer num){
        boolean[] visited = new boolean[num+1];
        visited[0] = true;
        visited[1] = true;
        for(int i=2; i*i<=num; i++){
            for(int j=i*i; j<=num; j+=i){
                if(!visited[j]) visited[j] = true;
            }
        }

        return visited;
    }
}
```

