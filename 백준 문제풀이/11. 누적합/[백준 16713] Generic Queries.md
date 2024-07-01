# Generic Queries 
https://www.acmicpc.net/problem/16713
| 시간 제한 | 메모리 제한 | 제출 | 정답 | 맞힌 사람 | 정답 비율 |
| :-------- | :---------- | :--- | :--- | :-------- | :-------- |
| 2.5 초    | 512 MB      | 1188 | 732  | 571       | 59.791%   |

## 문제

관영이는 쿼리를 좋아하고, XOR도 좋아한다. 그래서 관영이는 XOR을 이용한 쿼리 문제를 좋아한다.

길이가 𝑁$N$인 수열 𝑎1,𝑎2,⋯𝑎𝑁$a_1 , a_2 , \cdots a_N$이 있다. 

이제 관영이는 𝑄$Q$개의 쿼리에 답하려 한다. 각 쿼리는 𝑠𝑖,𝑒𝑖$s_i , e_i$ (1≤𝑠𝑖≤𝑒𝑖≤𝑁$1 \le s_i \le e_i \le N$)의 형태로 들어오고, 그 쿼리의 답은 𝑎𝑠𝑖,𝑎𝑠𝑖+1,⋯𝑎𝑒𝑖$a_{s_i}, a_{s_i+1}, \cdots a_{e_i}$을 모두 XOR한 값이다. 

 𝑄$Q$개의 쿼리가 들어올 때, 각 쿼리의 답을 모두 XOR한 결과를 구하시오. 

## 입력

첫째 줄에는 𝑁,𝑄$N, Q$가 공백을 사이에 두고 주어진다. (1≤𝑁≤106$1 \le N \le 10^6$, 1≤𝑄≤3⋅106$1 \le Q \le 3 \cdot 10^6$)

둘째 줄에는 𝑎1,𝑎2,⋯𝑎𝑁$a_1, a_2, \cdots a_N$이 공백을 사이에 두고 주어진다. (0≤𝑎𝑖≤109$0 \le a_i \le 10^9$)

그 후, 𝑄$Q$개의 줄에 걸쳐서, 각 줄마다 하나의 쿼리 𝑠𝑖,𝑒𝑖$s_i, e_i$가 공백을 사이에 두고 주어진다. (1≤𝑠𝑖≤𝑒𝑖≤𝑁$1 \le s_i \le e_i \le N$) 

## 출력

모든 쿼리의 답을 XOR한 값을 출력하시오. 

## 예제 입력 1 복사

```
5 3
4 4 4 4 4
1 1
1 2
1 3
```

## 예제 출력 1 복사

```
0
```

## 예제 입력 2 복사

```
5 4
4 4 2 1 0
1 1
1 2
1 3
2 4
```

## 예제 출력 2 복사

```
1
```



## 강의 풀이

* 누적 XOR 배열을 구한다.
* q번의 [s:e] 질문에 대해 누적 XOR 배열을 사용해 구간 XOR을 구함
* XOR
  * 5, 3 이라는 수가 있다면 해당 수를 각각 2진수로 바꾸고 각 자리수마다 아래와 같은 연산을 해 나온 값을 구하는 연산.
  * 같은 값이면 0, 다른 값이면 1
  * 0 ^ 0 = 0
  * 0 ^ 1 = 1
  * 1 ^ 0 = 1
  * 1 ^ 1 = 0

```java
package baekjoon;

import java.util.Scanner;

public class backjoon_16713 {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();
		int q = sc.nextInt();
		
		int[] arr = new int[n+1];
		
		for(int i=1; i<=n; i++) {
			arr[i] = sc.nextInt();
		}
		
		int[] acc = new int[n+1];
		
		// 1. 누적 XOR 배열을 구한다.
		for(int i=1; i<=n; i++) {
			acc[i] = acc[i-1] ^ arr[i];
		}
		
//		System.out.println(Arrays.toString(acc));
		
		// 2. q번의 [s:e] 질문에 대해 누적 XOR 배열을 사용해 구간 XOR을 구함
		int ans = 0;
		while(q-->0) {
			int s = sc.nextInt();
			int e = sc.nextInt();
			ans ^= acc[e] ^ acc[s-1];
		}
		
		System.out.println(ans);

	}

}
```

