# 이진 변환 반복하기

https://school.programmers.co.kr/learn/courses/30/lessons/70129



## 내 풀이

```python
class Solution {
    public int[] solution(String s) {
        int rotate = 0, removeZero = 0;
        
        while(!s.equals("1")){
            String reS = s.replace("0", "");
            
            removeZero += s.length() - reS.length();
            rotate++;
            
            s = Integer.toBinaryString(reS.length());
        }
        
        return new int[]{rotate, removeZero};
    }
}

```



