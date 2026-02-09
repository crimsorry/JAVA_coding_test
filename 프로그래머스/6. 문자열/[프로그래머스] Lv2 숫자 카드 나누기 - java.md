# 숫자 카드나누기

https://school.programmers.co.kr/learn/courses/30/lessons/135807?language=java



## 내 풀이

```java
class Solution {
    
    public int solution(int[] arrayA, int[] arrayB) {
        
        int gcdA = getGcdArray(arrayA);
        int gcdB = getGcdArray(arrayB);
        
        int answer = 0;
        
        if (isValid(gcdA, arrayB)) {
            answer = Math.max(answer, gcdA);
        }
        
        if (isValid(gcdB, arrayA)) {
            answer = Math.max(answer, gcdB);
        }
        
        return answer;
    }
    
    private int getGcdArray(int[] arr) {
        int gcd = arr[0];
        for (int i = 1; i < arr.length; i++) {
            gcd = gcd(gcd, arr[i]);
        }
        return gcd;
    }
    
    private int gcd(int a, int b) {
        while (b != 0) {
            int temp = a % b;
            a = b;
            b = temp;
        }
        return a;
    }
    
    private boolean isValid(int candidate, int[] otherArray) {
        if (candidate == 0) return false;
        
        for (int num : otherArray) {
            if (num % candidate == 0) {
                return false;
            }
        }
        return true;
    }
}

```



