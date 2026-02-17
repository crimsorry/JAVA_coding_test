# 음양 더하기

https://school.programmers.co.kr/learn/courses/30/lessons/76501

## **내 풀이**

```java
class Solution {
    public int solution(int[] absolutes, boolean[] signs) {
        int sum = 0;
        
        for (int i = 0; i < absolutes.length; i++) {
            if (signs[i]) {
                sum += absolutes[i];
            } else {
                sum -= absolutes[i];
            }
        }
        
        return sum;
    }
}

```
