## [프로그래머스] : 단어 변환

https://school.programmers.co.kr/learn/courses/30/lessons/43163

## 문제 설명

두 개의 단어 begin, target과 단어의 집합 words가 있습니다. 아래와 같은 규칙을 이용하여 begin에서 target으로 변환하는 가장 짧은 변환 과정을 찾으려고 합니다.

```
1. 한 번에 한 개의 알파벳만 바꿀 수 있습니다.
2. words에 있는 단어로만 변환할 수 있습니다.
```

예를 들어 begin이 "hit", target가 "cog", words가 ["hot","dot","dog","lot","log","cog"]라면 "hit" -> "hot" -> "dot" -> "dog" -> "cog"와 같이 4단계를 거쳐 변환할 수 있습니다.

두 개의 단어 begin, target과 단어의 집합 words가 매개변수로 주어질 때, 최소 몇 단계의 과정을 거쳐 begin을 target으로 변환할 수 있는지 return 하도록 solution 함수를 작성해주세요.

## 제한사항

- 각 단어는 알파벳 소문자로만 이루어져 있습니다.
- 각 단어의 길이는 3 이상 10 이하이며 모든 단어의 길이는 같습니다.
- words에는 3개 이상 50개 이하의 단어가 있으며 중복되는 단어는 없습니다.
- begin과 target은 같지 않습니다.
- 변환할 수 없는 경우에는 0를 return 합니다.

## 입출력 예

| begin | target | words                                      | return |
| ----- | ------ | ------------------------------------------ | ------ |
| "hit" | "cog"  | ["hot", "dot", "dog", "lot", "log", "cog"] | 4      |
| "hit" | "cog"  | ["hot", "dot", "dog", "lot", "log"]        | 0      |

## 입출력 예 설명

예제 #1
문제에 나온 예와 같습니다.

예제 #2
target인 "cog"는 words 안에 없기 때문에 변환할 수 없습니다.

## 내 풀이

![img](https://postfiles.pstatic.net/MjAyNTA5MjRfOSAg/MDAxNzU4NjkzNjIzMTMx.PC4kZY74QdEiujFOxQ6PYgz8X3NktuHTdKDtJ1axlnkg.WlxBSZuMNS-ZT8cippUUiDfPmNeh7pU43JdumGjOBu0g.PNG/image.png?type=w773)

```
import java.util.*;

class Solution {
    public static class Node{
		String word;
		int cnt;
		
		public Node(String word, int cnt) {
			this.word = word;
			this.cnt = cnt;
		}
	}
    
    public int solution(String begin, String target, String[] words) {
        int answer = 0;
        boolean bool = true;
        
        Queue<Node> q = new LinkedList<Node>();
        q.offer(new Node(begin, 0));
        
        for(int i=0; i<words.length; i++) {
        	if(words[i].equals(target)) {
        		bool = false;
        	}
        }
        
        if(bool) return 0;
        
//        System.out.println("begin: " + begin);
        
        while(!q.isEmpty()) {
			Node node = q.poll();
			
			if(node.word.equals(target)) {
				return node.cnt;
			}
			
			for(int i=0; i<words.length; i++) {
				int chk = 0;
				for(int j=0; j<words[i].length(); j++) {
					if(words[i].charAt(j) == node.word.charAt(j)) {
						chk++;
					}
				}
				if(chk == words[i].length()-1) {
					System.out.println("words[i]: " + words[i]);
					q.offer(new Node(words[i], node.cnt+1));
				}
				
			}
		}
        
        return answer;
    }
}
```

### 두번째 풀이

* 해당 문제의 경우 가장 `짧은 변환 과정`을 찾는 문제임으로 **BFS** 를 이용한 풀이가 적절
* 다만 이전 풀이과정에서 `visited` 를 활용한 방문처리 빠짐!

* visited 추가로 시간 복잡도 약 `50% 개선!`

![img](https://postfiles.pstatic.net/MjAyNTA5MjRfMTQ4/MDAxNzU4NjkzNTg0ODcy.l1mSjSFaKTk4Li1iWbSS1qEL9FmjsAKB9KMaNSOlbZcg.KYFdetxCg_9VWogxheBKsA65cEzVNgGhWZYa5GpllGkg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    public static int n;

    public static class Node{
        String word;
        int cnt;

        public Node(String word, int cnt){
            this.word = word;
            this.cnt = cnt;
        }
    }
    
    public int solution(String begin, String target, String[] words){
        n = begin.length();
        return bfs(begin, target, words);
    }
    
    public static int bfs(String begin, String target, String[] words){
        boolean[] visited = new boolean[words.length];
        Queue<Node> queue = new LinkedList<Node>();
        queue.offer(new Node(begin, 0));

        while(!queue.isEmpty()){
            Node cur = queue.poll();

            if(cur.word.equals(target)){
                return cur.cnt;
            }

            for(int i=0; i<words.length; i++){
                int same = 0;
                for(int j=0; j<n; j++){
                    if(cur.word.charAt(j) == words[i].charAt(j)){
                        same++;
                    }
                }
                if(same != n-1) continue;
                if(!visited[i]){
                    visited[i] = true;
                    queue.offer(new Node(words[i], cur.cnt+1));
                }
            }
        }
        return 0;
    }
}
```

### 세번째 풀이

* **DFS** 로 풀면 더 시간이 오래걸릴 것이라 예상하고 풀었으나...

* 예상과 달리 속도가 `10배 이상 개선` 된 것으로 확인. 메모리도 더 효율적....

  ![img](https://postfiles.pstatic.net/MjAyNTA5MjRfMzIg/MDAxNzU4Njk1Nzk0NjM4.-SwNHjfZqsL7e_bXjBq9VuKhSc880NCmcLpEeZcTSdQg.7-FgZXWbgdQaMvZSjelfUzkqFX1IbhQ5gDYCYb30DwMg.PNG/image.png?type=w773)

**WHY???**

> 모든 문제를 풀때 BFS 가 가장 빠르지 않다!

**현재 문제 상황:**

* 3 <= words <= 50
* 3 <= word.len <= 10

-> 크기와 길이 모두 작음!

BFS 를 이용해 Queue 에 넣는 경우 메모리/연산에서 낭비가 발생 할 수 있다

**결론:**

> **BFS: 크기가 크고, 최단 거리 뽑을때 유용**
> **DFS: 크기가 작은 경우 유리**

```java
import java.util.*;

class Solution {
    
    public static int n;
    public static int answer;
    
    public static int solution(String begin, String target, String[] words){
        n = begin.length();
        boolean[] visited = new boolean[words.length];
        answer = 0;
        dfs(begin, target, words, 0, visited);
        return answer;
    }

    public static void dfs(String begin, String target, String[] words, int chk, boolean[] visited){
        if(begin.equals(target)){
            if(answer == 0){
                answer = chk;
            } else{
                answer = Math.min(answer, chk);
            }
        }

        for(int i=0; i<words.length; i++){
            if(visited[i]) continue;

            int same = 0;
            for(int j=0; j<n; j++){
                if(begin.charAt(j) == words[i].charAt(j)){
                    same++;
                }
            }

            if(same != n-1) continue;

            visited[i] = true;
            dfs(words[i], target, words, chk+1, visited);
            visited[i] = false; // 백트래킹!
        }
    }
}
```

