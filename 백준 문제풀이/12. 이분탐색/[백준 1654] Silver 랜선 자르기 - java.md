# 랜선 자르기 

 https://www.acmicpc.net/problem/1654

## 내 풀이

1. 랜선 배열 선언
2. l = 0, r = (1L << 31) - 1 최대값 선언
   * 비트연산
   * 32비트 정수의 최댓값
3. 중앙값 m 선언
4. 각 랜선 / m 인 값을 더해 N과 같거나 큰 경우 ans
5. 이진탐색 수행
6. 정답 출력!

```java
package baekjoon;

import java.util.Scanner;

public class baekjoon_1654 {
	
	static int count(int[] arr, long m) {
		int cnt = 0;
		for(int length : arr) {
			cnt += (length/m);
		}
		return cnt;
	}

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		int K = sc.nextInt();
		int N = sc.nextInt();
		int[] arr = new int[K];
		
		for(int i=0; i<K; i++) {
			arr[i] = sc.nextInt();
		}
		
		long l = 0, r = (1L << 31) - 1, ans = 0;
		
		while(l <= r) {
			long m = (l + r) / 2;
			if(count(arr, m) >= N) {
				ans = m;
				l = m + 1;
			}else {
				r = m - 1;
			}
		}
		
		System.out.println(ans);
	}
}
```

### 두번째 풀이

* break 포인트 추가!

![img](https://postfiles.pstatic.net/MjAyNTEwMTNfOTcg/MDAxNzYwMzU4NjM0NzI3.g7saucu_2vCDHbivxFvzPMhWbIlCAdNQ3HviFuzSkmQg.xa1Bc9v6-i_9DNqlbsPb2iv80a6U95_jW0lJkeSZR2Yg.PNG/image.png?type=w773)

```java
package backjoon;

import java.util.Arrays;
import java.util.Scanner;

public class P_1654 {

    public static void main(String[] args) {

        long answer = 0;

        Scanner sc = new Scanner(System.in);

        int k = sc.nextInt();
        int n = sc.nextInt();
        int[] array = new int[k];

        for(int i=0; i<k; i++){
            array[i] = sc.nextInt();
        }

        long left = 1;
        long right = (long) Arrays.stream(array).max().getAsInt();

        while(left <= right){
            long mid = (left + right) / 2;
            long total = 0;

            for(int i=0; i<k; i++){
                total += (array[i] / mid);
                if(total >= n) break;
            }

            if(total >= n){
                left = mid + 1;
                answer = mid;
            }else{
                right = mid - 1;
            }
        }

        System.out.println(answer);

    }

}
```

