# **타겟 넘버 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/43165?language=java

## **내 풀이**

### **문제 풀이 흐름**

1. DFS 를 활용하여 각 깊이의 경우의 수를 구하기



### **주요 포인트**

```makefile
                 num=0   (시작)
                /      \
       +1      /        \     -1
              /          \
         num=1            num=-1
         /   \             /   \
     +1 /     \ -1     +1 /     \ -1
       /       \         /       \
  num=2       num=0   num=0     num=-2
    / \        / \     / \       / \
 +1 /   \ -1 /   \   +1/   \-1 /   \
   /     \   /     \   /     \   /     \
num=3  num=1 num=1 num=-1 num=1 num=-1 num=-3

```



### **결과**

![img](https://postfiles.pstatic.net/MjAyNTA5MDFfMjU1/MDAxNzU2NzExNTY5MTUy.HOw7Zwjma-NX_i6orFtCsI4uiHVjacI5pTBW-YF0SKwg.ZMi8B_Y2Rm_371mYNCmWTXYl25JDNN86Q5WvGWpLHgIg.PNG/image.png?type=w773)

### **내 코드**

```java
package programmers;

public class p43165 {

    static int answer = 0;

    public static void dfs(int[] numbers, int target, int cnt, int sum){
        if(cnt == numbers.length){
            if(sum == target){
                answer++;
            }
            return;
        }

        dfs(numbers, target, cnt+1, sum+numbers[cnt]);
        dfs(numbers, target, cnt+1, sum-numbers[cnt]);
    }

    public static int solution(int[] numbers, int target) {
        dfs(numbers, target, 0, 0);
        return answer;
    }

    public static void main(String[] args) {

        int[] numbers = {1, 1, 1, 1, 1};
        int target = 3;

        System.out.println(solution(numbers, target));
    }
}
```

### 