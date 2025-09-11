

# **여행경로 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/43164

## **내 풀이**

### **문제 풀이 흐름**

* **DFS** 로 풀기
* why? 모든 경로를 탐색해야 하기때문에 최단 거리문제 X
* 모두 같은 거리임으로 queue 를 사용하게 되면 오히려 속도가 더 걸릴 것으로 예상.
* 내 예상이 맞는지 코드를 통해 확인해보자.



### **내 코드**

* DFS 풀이

![img](https://postfiles.pstatic.net/MjAyNTA5MjRfMjA3/MDAxNzU4NzAwNTkyNDM1.cdZR79VECCz5boJGzy92pf6_fX3PWMFJ6yUQGWZQJw4g.qeJ3ANaFj3lwgTjP38ETFgBSjVH3Uj99ML1eOQvFQLAg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    
    public static ArrayList<String> answer;

    public static String[] solution(String[][] tickets){
        ArrayList<String> routes = new ArrayList<String>();
        routes.add("ICN");
        dfs(tickets, new boolean[tickets.length], routes);
        return answer.toArray(new String[0]);
    }

    public static void dfs(String[][] tickets, boolean[] visited, ArrayList<String> routes){
        String route = routes.get(routes.size()-1);

        if(routes.size()-1 == tickets.length){
            if(answer == null){
                answer = new ArrayList<>(routes);
            }else{
                String r1 = String.join("", routes);
                String r2 = String.join("", answer);

                if(r1.compareTo(r2) <0){
//                    answer = routes; // 얕은 복사 (주소 값 복사됨)
                    answer = new ArrayList<>(routes); // 깊은 복사
                }
            }
        }

        for(int i=0; i<tickets.length; i++){
            if(tickets[i][0].equals(route) && !visited[i]){
                visited[i] = true;
                routes.add(tickets[i][1]);
                dfs(tickets, visited, routes);
                visited[i] = false;
                routes.remove(routes.size()-1);
            }
        }

    }
}
```

### 두번째 풀이 

* 다음으로 **BFS** 를 통해 풀이를 이어나갔다.
* 첫번째로 고려한 점은 사전순 정렬을 통해 넓이 탐색을 가능하게끔 하자 였다.
* 두번째로 고려한 점은 visited 였다. 처음에는 Node 에 route, cnt 를 둬서 각 route 의 횟수를 더하는 방식으로 최적의 경우를 구하려 하였지만 `tickets[i][0]` 이 같은 경우, 방문을 하지 못하는 문제점이 발생하였다.
* 따라서 Node 에 visited[] 역시 변수로 선언하여 푼 결과 답을 구할 수 있었다.
* 역시나 처음 예상했던 것 과 같이 DFS 보다 성능이 떨어지는 결과가 나타났다.

![img](https://postfiles.pstatic.net/MjAyNTA5MjVfMjQ0/MDAxNzU4ODA0NDU5Mjgy.17CTr_XZzBLN4W1hgcdZYhsrXmhL_yP11YP1pg_37Jkg.9TbD2V-uYzy4FKunLjfap7CP_NUJgkG-qwBt80RQLlQg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    
    public static String[] solution(String[][] tickets){
        Arrays.sort(tickets, Comparator.comparing(a -> a[1]));
        return bfs(tickets);
    }

    public static String[] bfs(String[][] tickets){
        Queue<Node> queue = new LinkedList<>();
        queue.offer(new Node(new ArrayList<>(List.of("ICN")), new boolean[tickets.length]));

        while(!queue.isEmpty()){
            Node cur = queue.poll();

            if(cur.route.size() == tickets.length + 1){
                return cur.route.toArray(new String[0]);
            }

            for(int i=0; i<tickets.length; i++){
                if(!cur.visited[i] && tickets[i][0].equals(cur.route.get(cur.route.size()-1))){
                    boolean[] newVisited = cur.visited.clone(); // 복사
                    newVisited[i] = true;

                    ArrayList<String> newRoute = new ArrayList<>(cur.route);
                    newRoute.add(tickets[i][1]);

                    queue.offer(new Node(newRoute, newVisited));
                }
            }
        }
        return new String[0];
    }
    
    static class Node {
        ArrayList<String> route; 
        boolean[] visited;       

        public Node(ArrayList<String> route, boolean[] visited) {
            this.route = route;
            this.visited = visited;
        }
    }

}
```





### 