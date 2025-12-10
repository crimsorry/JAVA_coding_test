

# JadenCase 문자열 만들기

https://school.programmers.co.kr/learn/courses/30/lessons/12951

## 내 풀이

```python
import java.io.*;

class Solution {
    public String solution(String s) {
        StringBuilder sb = new StringBuilder();

        s = s.toLowerCase();

        int chk = -1;

        for(int i = 0; i<s.length(); i++){
            char c = s.charAt(i);
            if(chk == -1){
                if(c - 'a' >= 0){
                    c = (char) (c - 'a' + 'A');
                }
                chk = 0;
            }
            if(c == ' '){
                chk = -1;
            }
            sb.append(c);
        }

        return sb.toString();
    }
}
```



