# 카드

https://www.acmicpc.net/problem/11652

## 내 풀이

* 최빈값 구하기!
* Arrays.sort 를 통해 오름차순 정렬
  * 앞선 수가 무조건 뒷 수 보다 작음!


```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Arrays;

public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(br.readLine());
        long[] arr = new long[n];

        for(int i=0; i<n; i++){
            arr[i] = Long.parseLong(br.readLine());
        }

        Arrays.sort(arr);

        long su = arr[0]; // 많이 가진 장수의 수
        int maxCnt = 1; // 많이 가진 장수
        int currentCnt = 1;

        for(int i=1; i<n; i++){
            if(arr[i] == arr[i-1]){
                currentCnt++;
            }else{
                currentCnt = 1;
            }

            if(currentCnt > maxCnt){
                maxCnt = currentCnt;
                su = arr[i];
            }
        }

        System.out.println(su);

    }
}

```
