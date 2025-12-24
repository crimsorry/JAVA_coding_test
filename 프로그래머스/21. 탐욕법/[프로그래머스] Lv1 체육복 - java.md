## 체육복

https://school.programmers.co.kr/learn/courses/30/lessons/42862

## 내 풀이

```java
import java.util.*;
import java.util.stream.*;

class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int[] arr = new int[n+1];
        
        for(int i=1; i<=n; i++){
            arr[i] = 1;
        }
        
        for(int r : reserve){
            arr[r]++;
        }
        
        for(int l : lost){
            arr[l]--;
        }
        
        for(int i=1; i<=n; i++){
            if(arr[i] == 0){
                if(i > 1 && arr[i-1] == 2){
                    arr[i-1]--;
                    arr[i]++;
                } else if(i < n && arr[i+1] == 2){
                    arr[i+1]--;
                    arr[i]++;
                }
            }
        }
        
        int answer = 0;
        for(int i = 1; i <= n; i++){
            if(arr[i] >= 1) answer++;
        }
        
        return answer;
    }
    
    
}
```

