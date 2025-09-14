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

### 두번째 풀이

* 코드 효율성을 높이기 위해 수정
* brown 사이에 yellow 가 1줄 들어가게 때문에 height 가 3 이상 이여야 한다.

![img](https://postfiles.pstatic.net/MjAyNTA5MjlfMTQy/MDAxNzU5MTM0MDA3NDY2.s_ow38C91L-fEI2vH9AzuQwgajks7s6L6esoHQg232wg.H8ZP6xHNhOndaP8wEd1PR0JPwu1j-HYPhN9UT28L6SQg.PNG/image.png?type=w773)

```java
class Solution {
    public static int[] solution(int brown, int yellow){

        int total = brown + yellow;

        for(int height=3; height<=total; height++){
            if(total % height == 0){
                int width = total / height;
                if(width >= height && yellow == (width-2) * (height-2)){
                    return new int[]{width, height};
                }
            }
        }

        return new int[2];
    }
}
```

