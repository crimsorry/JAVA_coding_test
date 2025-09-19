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

### 두번째 풀이

* **에라토스테네스의 체** 를 더욱 효율적으로 풀기

* 왜 `i * i <= n` 까지만 볼까?

* 어떤 수의 합성수 중 가장 작은 값들의 집합은 늘 √n 이하다.

  > 합성수:  **“두 수의 곱”**
  >
  > 36 = 2 × 18
  >
  > 36 = 3 × 12
  >
  > 36 = 4 × 9
  >
  > 36 = 6 × 6
  >
  > 작은 수의 집합은 √36 = 6 이하!

* 이를 Java 에서는 i * i <= n 로 표현!

![img](https://postfiles.pstatic.net/MjAyNTEwMDFfMjUg/MDAxNzU5MzIyMDU5ODk4.lOO0FE80XDVkqVjoPRuzoOwt2_Z9uZG8fI2yNgYxIIgg.7jiIUyX7n6yze5BAH43z_yhFQt1Pus9_2cgUx0YTdFYg.PNG/image.png?type=w773)

```java
class Solution {
    public static int solution(int n){
        int answer = 0;
        boolean[] visited = new boolean[n+1];

        for (int i = 2; i * i <= n; i++) {
            if (!visited[i]) {
                for (int j = i * i; j <= n; j += i) {
                    visited[j] = true;
                }
            }
        }

        for (int i = 2; i <= n; i++) {
            if (!visited[i]) answer++;
        }

        return answer;
    }
}
```

