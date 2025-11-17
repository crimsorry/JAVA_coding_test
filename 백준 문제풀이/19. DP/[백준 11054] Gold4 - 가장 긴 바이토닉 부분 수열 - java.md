# 가장 긴 바이토닉 부분 수열

https://www.acmicpc.net/problem/11054

## 내 풀이

* 부분 수열 구하기
  * 1, 2, 3 ... increase 되는 부분 수열 최대 값 집합 구하기
  * 오른쪽에서부터 5, 4, 3 .... decrease 되는 부분 수열 최대값 집합 구하기

* 각 집합의 i 번째를 더한값에서 -1 시키기!
  * 왜??
    * 각 집합의 최대값을 더함으로써 자기 자신을 각각 한번씩 더했기 때문. (+2 가 들어간 셈!)
    * 따라서 -1 시켜주기


```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] su = new int[n];

        for(int i=0; i<n; i++){
            su[i] = sc.nextInt();
        }

        int[] dpi = new int[n];
        int[] dpd = new int[n];

        for(int i=0; i<n; i++){
            dpi[i] = 1;
            for(int j=0; j<i; j++){
                if(su[i] > su[j]){
                    dpi[i] = Math.max(dpi[i], dpi[j]+1);
                }
            }
        }

        for(int i=n-1; i>=0; i--){
            dpd[i] = 1;
            for(int j=n-1; j>=i; j--){
                if(su[i] > su[j]){
                    dpd[i] = Math.max(dpd[i], dpd[j]+1);
                }
            }
        }

        int answer = 0;

        for(int i=0; i<n; i++){
            answer = Math.max(answer, dpi[i] + dpd[i] - 1);
        }

        System.out.println(answer);

    }

}
```

