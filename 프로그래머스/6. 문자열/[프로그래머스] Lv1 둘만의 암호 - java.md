# 둘만의 암호

https://school.programmers.co.kr/learn/courses/30/lessons/155652



## 내 풀이

```python
class Solution {
    public String solution(String s, String skip, int index) {
        StringBuilder answer = new StringBuilder();
        char[] skipArr = skip.toCharArray();

        for (char c : s.toCharArray()) {
            int moved = 0;
            char cur = c;

            while (moved < index) {
                cur++;
                if (cur > 'z') cur = 'a';

                boolean isSkip = false;
                for (char sc : skipArr) {
                    if (cur == sc) {
                        isSkip = true;
                        break;
                    }
                }

                if (!isSkip) {
                    moved++;
                }
            }
            answer.append(cur);
        }
        return answer.toString();
    }
}
```



