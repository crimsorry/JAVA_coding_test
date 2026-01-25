# 124나라의 숫자

https://school.programmers.co.kr/learn/courses/30/lessons/12899



## 내 풀이

```python
class Solution {
    public String solution(int n) {
        StringBuilder sb = new StringBuilder();

        while (n > 0) {
            int mod = n % 3;

            if (mod == 0) {
                sb.append("4");
                n = n / 3 - 1;
            } else if (mod == 1) {
                sb.append("1");
                n = n / 3;
            } else if (mod == 2) {
                sb.append("2");
                n = n / 3;
            }
        }

        return sb.reverse().toString();
    }
}
```



