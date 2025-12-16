# 두 용액 

 https://www.acmicpc.net/problem/2470

## 강의 풀이

* 첫번째 인덱스 arr 와 나머지 arr의 중앙값부터 0과 가까운지 비교
  * -99 | -2 -1 4 98
  * -99 와 4 의 절대값 구하기
  * 99 와 95를 비교하면서 같은 경우 return 절대값, 다른경우 이분 탐색 진행
* 시간복잡도: O(NlogN)

```java
package baekjoon;

import java.util.Arrays;
import java.util.Scanner;

public class baekjoon_2470 {
	
	static int findOptimalPair(int[] arr, int leftIndex, int rightIndex, int findValue) {
		int nearestValue = arr[leftIndex];
		int nearestDiff = Math.abs(findValue - nearestValue);
		int l = leftIndex+1, r = rightIndex;
		while(l <= r) {
			int m = (l + r) / 2;
			int diff = Math.abs(findValue - arr[m]);
			if (diff < nearestDiff) {
                nearestValue = arr[m];
                nearestDiff = diff;
            }
            if (arr[m] < findValue) l = m + 1;
            else if (arr[m] > findValue) r = m - 1;
            else return findValue;
		}
		return nearestValue;
	}

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		
		int[] arr = new int[N];
		
		for(int i=0; i<N; i++) {
			arr[i] = sc.nextInt();
		}
		
		Arrays.sort(arr);
		
		int ansAbs = Math.abs(arr[0] + arr[1]);
		int ansX = 0;
		int ansY = 0;
		for(int i=0; i<N-1; i++) {
			int pairValue = findOptimalPair(arr, i+1, N-1, -arr[i]);
			int sumAbs = Math.abs(arr[i] + pairValue);
            if (ansAbs > sumAbs) {
                ansAbs = sumAbs;
                ansX = arr[i];
                ansY = pairValue;
            }
        }
        System.out.println(ansX + " " + ansY);
	}

}

```





### 두번쨰 풀이

* TreeSet 사용
* set.floor(x)
  * 이 값과 가장 가깝되, 이 값 이하인 가장 가까운 숫자 찾아서 return 
  * 해당 값이 없다면 null
* set.ceiling(x)
  * 이 값과 가장 가깝되, 이 값 이상인 가장 가까운 숫자 찾아서 return
  * 해당 값이 없다면 null
* 시간복잡도: O(NlogN)
* 문제가 수정됐는지 해당 코드로는 시간 초과가 뜬다.

```
package baekjoon;

import java.util.Scanner;
import java.util.TreeSet;

public class baekjoon_2470 {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		int N = sc.nextInt();
		
		TreeSet<Integer> set = new TreeSet<>();
		
		int ansAbs = 2000000001;
		int ansX = 0;
		int ansY = 0;
		while(N-- > 0) {
			int x = sc.nextInt();
			Integer[] pairValues = {set.floor(-x), set.ceiling(-x)};
			for(Integer pairValue : pairValues) {
				if(pairValue == null) continue;
				int sumAbs = Math.abs(x + pairValue);
				if(sumAbs < ansAbs) {
					ansAbs = sumAbs;
					ansX = x;
					ansY = pairValue;
				}
			}
			set.add(x);
		}
		
		System.out.println(Math.min(ansX, ansY) + " " + Math.max(ansX, ansY));
		
	}
}

```



## 내 풀이

* 합이 양수: r--
  * 더 작은 수를 찾아야 하기 때문!
* 합이 음수: l++
  * 더 큰 수를 찾아야 하기 때문!

```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        long[] arr = new long[n];

        for(int i=0; i<n; i++){
            arr[i] = sc.nextInt();
        }

        Arrays.sort(arr);

        int l = 0;
        int r = n-1;
        int answerL = l;
        int answerR = r;
        long answer = Long.MAX_VALUE;

        while(l < r){
            long mid = arr[l] + arr[r];
            long absMid = Math.abs(mid);

            if(absMid<answer){
                answer = absMid;
                answerL = l;
                answerR = r;
            }

            if(mid < 0){
                l++;
            }else if(mid > 0){
                r--;
            }else{
                break;
            }
        }

        System.out.printf("%d %d", arr[answerL], arr[answerR]);

    }

}

```

