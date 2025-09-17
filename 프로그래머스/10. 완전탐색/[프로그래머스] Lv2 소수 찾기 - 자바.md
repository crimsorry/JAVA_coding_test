# **소수찾기 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/12921?language=java

## **내 풀이**

### **문제 풀이 흐름**

에라토스체의 원리 이용

1. 0과 1은 소수가 아니므로 제외
2. 가장 작은 소수인 2 선택 후 2의 배수 제외
3. 다음 소수인 3 선택 후 3의 배수 제외
4. 그 다음 남아있는 수인 5 선택 후 5의 배수 제외
5.  .... 이렇게 영원히 제외 후 남은 수가 소수!

### **내 코드**

![img](https://postfiles.pstatic.net/MjAyNTEwMDFfMiAg/MDAxNzU5MzA3NDAxNTA1.T9AXJnfWIlpv5FfhvwLA5xXKqm9HEB8ig2UVEyf-M3Ig.ZopCG7VmeRQNZQHxy5r-uOrepD1kHTBZydq_4CrAe1Yg.PNG/image.png?type=w773)

```java
class Solution {
    public static int solution(int n){
        int answer = 0;

        boolean[] visited = new boolean[n+1];
        for(int i=0; i<n+1; i++){
            visited[i] = true;
        }

        for(int i=2; i<n; i++){
            int j = i + i;
            while(j<=n){
                if(visited[j]) visited[j] = false; // 배수는 소수가 아님!
                j+=i;
            }
        }

        for(int i=2; i<n+1; i++){
            if(visited[i]) answer++;
        }

        return answer;
    }
}
```

### 