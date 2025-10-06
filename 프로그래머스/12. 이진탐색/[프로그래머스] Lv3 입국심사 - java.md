## [프로그래머스] : 입국심사

https://school.programmers.co.kr/learn/courses/30/lessons/43238?gad_source=1&gad_campaignid=22356298761&gbraid=0AAAAAC_c4nBAiK8Ox9wBzT8M1a__vQDXj&gclid=Cj0KCQjw0Y3HBhCxARIsAN7931Uyw3wOFwbuwKF0GszjfeoDMzG1DiAcLfsYE8sHTv7kYHf6uvDsy0YaAv_REALw_wcB

## 내 풀이

1. 배열 오름차순 정렬 (이진탐색은 오름차순 정렬 필수!)

2. left(초기값: 최소 기다리는 시간 0), right(초기값: 최대 기다리는 시간) 선언

3. left가 right와 같거나 작아질때 까지 while 문 돌리기

4. mid(가운데 숫자) 선언

5. people(검사한 사람 수) 선언

6. times 배열 수 만큼 for문 돌리기

7. 각각 분마다 들어갈 수 있는 사람 수를 구해서 poeple에 담기

8. 만약에 심사해야될 사람보다 적게 검사했을 경우 left 값에 mid+1 값 담기

9. 심사 해야될 사람보다 크거나 같게 검사했을 경우 right 값에 mid-1 값 담고 answer에 mid 담기

10. 값 출력!

    ![img](https://postfiles.pstatic.net/MjAyNTEwMDZfMTEx/MDAxNzU5NzUzMTMyODAw.LP44p4Jv1E_dhaAvwdMzggYTt8usGixhhbm1Yszd21Mg._elBJ2b8UjynzHXl30q7d737rTEd_lojE90hN7zBFoUg.PNG/image.png?type=w773)

```java
import java.util.*;

// 이진탐색
class Solution {
    public long solution(int n, int[] times) {
        
        Arrays.sort(times); // 오름차순 정렬
        
        long answer = 0;
        long left = 0; // 왼쪽
        long right = (long)n * times[times.length-1]; // 오른쪽 # 최대 기다리는 시간
        
        while(left<=right){
            long mid = (left+right)/2;
            long people = 0;
            
            for(int i=0; i<times.length; i++){
                people += mid/times[i]; // 각각 분마다 들어갈 수 있는 사람 수
            }
            
            if(people<n){ // 심사 해야될 사람보다 적게 검사함 # 수가 큼!
                left = mid + 1; // 수가 크면 이진탐색에서 mid+1
            }else{
                right = mid - 1; // 수가 작으면 이진탐색에서 mid-1
                answer = mid; // 이진탐색에서 가운데 수 구함
            }
        }
        
        return answer;
    }
}
```

### 두번째 풀이

* 불필요한 반복을 방지하여 효율성 증대!
* 하지만 유의미한 결과값은 아닌 느낌...!

![img](https://postfiles.pstatic.net/MjAyNTEwMDZfMTY0/MDAxNzU5NzUzMDcwNDU1.JK5DjVu-42HH4e0xqEn66nYOlwBMgSUviUE3fSG7oWEg.AFfCkcGbf6fI3ajcPpbx_U9aH_OmGkChVja2LFj-kDkg.PNG/image.png?type=w773)

```java
import java.util.*;

class Solution {
    public static long solution(int n, int[] times){
        long answer = 0;
        long left = 1; // 최소 시간
        long right = (long) Arrays.stream(times).max().getAsInt() * n; // 최악 시간

        while(left <= right){
            long mid = (left + right) / 2;
            long total = 0;
            for(int i=0; i<times.length; i++){
                total += mid / times[i];
                if (total >= n) break; 
            }

            if(total >= n){
                right = mid - 1; // 짧은 시간 도전
                answer = mid;
            }else{
                left = mid + 1; // 긴 시간 도전
            }
        }

        return answer;
    }
}
```

