## 회의실 배정

https://www.acmicpc.net/problem/1931

## 내 답안

* 정렬
  1. 회의 끝나는 시간 기준 정렬
  2. 회의 끝나는 시간이 같다면 회의 시작 시간 기준 정렬
* 회의 시작하는 시간이 직전 끝나는 시간보다 큰 경우 ++

![img](https://postfiles.pstatic.net/MjAyNTEwMjdfMjcy/MDAxNzYxNTcxNDA3Mjk5.2r1unTdc2aS9PLcVRs3k43MkFbCbeO-y8skJotYREq0g.CmRiS4BRZ1AqQ1zDrN1SCrcXNtHuWM7EAZ2ze-4GTlIg.PNG/image.png?type=w773)

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[][] meeting = new int[n][2];
        int answer = 0;
        int last = 0;

        for(int i=0; i<n; i++){
            meeting[i][0] = sc.nextInt();
            meeting[i][1] = sc.nextInt();
        }

        Arrays.sort(meeting, (s, e) -> {
            if(s[1] == e[1]) return Integer.compare(s[0], e[0]);
            return Integer.compare(s[1], e[1]);
        });

        for(int i=0; i<n; i++){
            if(meeting[i][0] >= last) {
                answer++;
                last = meeting[i][1];
            }
        }

        System.out.println(answer);

    }

}

```



