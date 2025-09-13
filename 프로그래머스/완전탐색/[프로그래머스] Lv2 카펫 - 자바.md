# **카펫 - 자바**

https://school.programmers.co.kr/learn/courses/30/lessons/42842

## **내 풀이**

### **문제 풀이 흐름**

1. left, right 변수를 선언
2. 공간의 크기를 지속적으로 비교하면서 크기 줄여나가기
3. yellow = (left-2)*(right-2)

### **내 코드**

![img](https://postfiles.pstatic.net/MjAyNTA5MjlfMjYg/MDAxNzU5MTMzMDA2NDM5.cIg_lGNfgZlGvC31RQG_7ZgKOAogM2RflJhiLQhYLmcg.IFZ2YGYKA2EweAkQoWOaQAzRozYuKNS3pvtLRPJjHiQg.PNG/image.png?type=w773)

```java
class Solution {
    public static int[] solution(int brown, int yellow){

        int n = brown + yellow;
        int l = n-1;
        int r = 1;

        while(true){
            int m = l*r;
            if(m==n) {
                if(yellow==(l-2)*((r-2))){
                    break;
                }else{
                    l--;
                    r = 1;
                }
            }else if(m<n){
                r++;
            }else if(m>n){
                l--;
                r = 1;
            }
        }

        int[] answer = {l, r};

        return answer;
    }
}
```

