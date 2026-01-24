# N개의 최소공배수

https://school.programmers.co.kr/learn/courses/30/lessons/12953



## 내 풀이

```python
class Solution {
    public int solution(int[] arr) {
        int result = arr[0];

        for (int i = 1; i < arr.length; i++) {
            result = lcm(result, arr[i]);
        }

        return result;
    }

    private int lcm(int a, int b) {
        return a * b / gcd(a, b);
    }

    private int gcd(int a, int b) {
        while (b != 0) {
            int temp = a % b;
            a = b;
            b = temp;
        }
        return a;
    }
}
```



