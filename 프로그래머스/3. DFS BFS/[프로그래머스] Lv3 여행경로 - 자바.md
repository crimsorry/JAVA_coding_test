

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



### 궁금증!

BFS 로 문제를 풀다가 Node 클래스를 가장 상단에 두어 성능테스트를 돌려보았다. 

```java
class Solution {

    static class Node {
        ArrayList<String> route; 
        boolean[] visited;       

        ...
    }
    
    public static String[] solution(String[][] tickets){
        ...
    }

}
```



당연히 같은 결과가 나올 것이라 생각하며 결과를 기다리는데...



![img](https://postfiles.pstatic.net/MjAyNTA5MjVfMjk1/MDAxNzU4ODA0NDI0Mzc3._Qhz4zyXKhnlIoq-xFSIl8DsckcvqBCYIVbURReOjQwg.CmrCHzh4utsJaFbYxAmLv2PA6yEocFnUaMZf-DD7GO0g.PNG/image.png?type=w773)



Node 클래스를 아래에 두었을때 보다 시간, 메모리가 증가하는 결과가 나왔다!



이 결과는 **Node 클래스 위치 자체 때문이 아니라**, JVM 내부 동작과 최적화 타이밍 때문에 발생하는 것으로 보인다.

1. **클래스 로딩(Class Loading)**
   - JVM은 클래스를 처음 참조할 때 로딩 및 초기화를 수행
   - `Node`의 위치가 달라지면 참조 시점이나 최적화 타이밍이 미묘하게 달라질 수 있음
2. **JIT 컴파일러 최적화**
   - JVM은 처음에는 인터프리터로 코드를 실행하고, 반복 실행되는 메서드를 JIT으로 컴파일
   - `Node` 객체 생성이 BFS 루프에서 매우 자주 발생하기 때문에, 언제 JIT 최적화가 적용되는지에 따라 실행 시간이 달라질 수 있음
3. **Escape Analysis**
   - JIT은 객체가 메서드 내부에서만 사용되면 스택에 할당하는 최적화를 적용할 수 있다.
   - `Node` 사용 패턴에 따라 이 최적화가 적용되거나 적용되지 않을 수 있으며, 미세한 성능 차이를 만들 수 있음



그래서 결론은??

- **Node 선언 위치가 본질적으로 성능에 영향을 주는 것은 아님**
- 실행 시간 차이는 JVM 최적화 타이밍 및 서버 환경(부하, 캐시, JIT warm-up 등)에 따른 **측정 노이즈**!!!
- 즉, 코드 구조보다 **실행 환경 요인**이 큼!

------

## 참고 자료

- [How the JIT compiler boosts Java performance in OpenJDK (Red Hat)](https://developers.redhat.com/articles/2021/06/23/how-jit-compiler-boosts-java-performance-openjdk?utm_source=chatgpt.com)
- [Tiered Compilation in JVM (Baeldung)](https://www.baeldung.com/jvm-tiered-compilation?utm_source=chatgpt.com)
- [Java Class Loading – Performance Impact (Reddit)](https://www.reddit.com/r/java/comments/wvl7yh/java_class_loading_performance_impact/?utm_source=chatgpt.com)