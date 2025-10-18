# 가장 긴 증가하는 부분 수열

https://www.acmicpc.net/problem/11053

## 내 풀이

* **수열** 이란?
  * 일정한 규칙에 따라 한 줄로 배열된 수의 열


* **부분 수열** 이란?

  * 수열의 일부 항들을 순서를 바꾸지 않고 선택하여 만든 새로운 수열
  * ex)
    * A = `[10, 20, 10, 30, 20, 50]`
    * 가능한 **부분 수열** :
      - `[10]`
      - `[10, 20]`
      - `[10, 30, 50]`
      - `[10, 20, 30, 50]`  <<< 가장 김!!
      - `[20, 30, 50]`

* 따라서 답을 구하기 위해선?

  > i 번째에서 구할 수 있는 가장 긴 조합을 구하기!!!!!

처음엔 연속된 수를 구해야 한다고 생각해 `for(int j=i; i<n; j++)` 로 구했는데 이게 큰 패착이였음....

![img](https://postfiles.pstatic.net/MjAyNTEwMTlfMjY3/MDAxNzYwODAxMjU3MTA5._5wErRBBATLZq2XYgM7k3_Q-0E0C21zxFkI6qQXFLaUg.WzJsHtAQFPV-lMUJMKJq5sOpjcw2ZFSYB88Ix5632v0g.PNG/image.png?type=w773)

```java
import java.util.*;

public class Main {
    
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] array = new int[n];

        for(int i=0; i<n; i++){
            array[i] = sc.nextInt();
        }

        int[] dp = new int[n];
        
        for(int i=0; i<n; i++){
            dp[i] = 1;
            for(int j=0; j<i; j++){
                if(array[i] > array[j]){
                    dp[i] = Math.max(dp[i], dp[j]+1);
                }
            }
        }

        System.out.println(Arrays.stream(dp).max().getAsInt());
    }
}
```

