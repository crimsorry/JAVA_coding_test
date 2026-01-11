# k진수에서 소수 개수 구하기

https://school.programmers.co.kr/learn/courses/30/lessons/92335



## 내 풀이

```python
class Solution {
    public int solution(int n, int k) {
        StringBuilder sb = new StringBuilder();
        while (n > 0) {
            sb.append(n % k);
            n /= k;
        }
        String baseK = sb.reverse().toString();

        int count = 0;
        String[] parts = baseK.split("0");
        for (String p : parts) {
            if (p.isEmpty()) continue;

            long val = Long.parseLong(p);
            if (isPrime(val)) count++;
        }
        return count;
    }

    private boolean isPrime(long x) {
        if (x < 2) return false;
        if (x == 2) return true;
        if (x % 2 == 0) return false;

        for (long i = 3; i * i <= x; i += 2) {
            if (x % i == 0) return false;
        }
        return true;
    }
}
```



