# 숫자의 표현

https://school.programmers.co.kr/learn/courses/30/lessons/12924



## 내 풀이

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
        int left = 1;
        int right = 1;
        int sum = 1;

        while(left<=n){
            if(sum<n){
                right++;
                sum+=right;
            }else if(sum==n){
                answer++;
                sum-=left;
                left++;
            }else{
                sum-=left;
                left++;
            }
        }

        return answer;
    }
}
```



