# 2개 이하로 다른 비트

https://school.programmers.co.kr/learn/courses/30/lessons/77885



## 내 풀이

```java
class Solution {
    public long[] solution(long[] numbers) {
        long[] answer = new long[numbers.length];

        for (int i = 0; i < numbers.length; i++) {
            long x = numbers[i];

            if (x % 2 == 0) {
                answer[i] = x + 1; // 짝
            } else {
                answer[i] = x + 1 + ((x ^ (x + 1)) >> 2); // 홀
            }
        }
        return answer;
    }
}
```



