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

### 두번째 풀이

* 에라토스테네스의 체 에는 두가지 풀이 방법 존재
  1. 첫번째 풀이와 같이 배열을 지정해 모든 소수 구하기
  2. 개별 소수 구하기
* 해당 문제의 경우 최악의 경우 visited 배열의 크기가 7자리 이상이 될 수 도 있음. 메모리 및 속도 증가!
* 따라서 개별 소수 구하는 방법을 통해 속도를 줄여나가기로 함
* 또한 **HashSet** 을 사용하여 시간복잡도 줄임
* 결과적으로 **성능 3배 이상 증가!**

![img](https://postfiles.pstatic.net/MjAyNTEwMDJfMjk5/MDAxNzU5MzMxMTM5NzYy.SO1vV8X2Tj7ieENzgZZf4o7DDYyc1nY5Fl7dp7cDDkUg.X7R-xgbE16N3Z735fy4SzD_RBHFxpCJqDt08dgKp6Tkg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    
    public static HashSet<Integer> hashSet = new HashSet<Integer>();

    public static int solution(String numbers){
        int cnt = 0;
        String[] nums = numbers.split("");

        dfs(nums, new boolean[nums.length+1], "");

        for(Integer num : hashSet){
            if(isPrime(num)) cnt++;
        }

        return cnt;
    }

    public static void dfs(String[] nums, boolean[] visited, String num){
        if(!num.isEmpty()){
            hashSet.add(Integer.parseInt(num));
        }

        for(int i=0; i<nums.length; i++){
            if(!visited[i]){
                visited[i] = true;
                dfs(nums, visited, num + nums[i]);
                visited[i] = false;
            }
        }
    }

    public static boolean isPrime(int num){
        if(num < 2) return false;
        if(num == 2) return true;
        if(num % 2 == 0) return false;
        for(int i=3; i*i<=num; i+=2){
            if(num % i == 0) return false;
        }
        return true;
    }
}
```

