# 압축

https://school.programmers.co.kr/learn/courses/30/lessons/60057



## 내 풀이

```python
import java.util.*;

class Solution {
    public int solution(String s) {
        int answer = 0;
        
        int maxIndex = s.length()/2;
        int index = 1;
        int[] arr = new int[s.length()+1];
        
        while(index <= maxIndex){
            int cnt = 0;
            int total = 0;
            String past = "";
            
            for(int i=0; i<s.length() - index; i+=index){
                String current = "";
                for(int j=i; j<i+index; j++){
                    current += s.charAt(j);
                }
                if(current.equals(past)){
                    if(cnt == 0){
                        cnt++;
                    }
                }else{
                    past = current;
                    total = cnt + 1;
                    cnt = 0;
                }
            }
            arr[index] = cnt;
            index++;
        }
        
        System.out.println(Arrays.toString(arr));
        
        
        
        return answer;
    }
}
```



