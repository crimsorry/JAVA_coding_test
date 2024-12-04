## [이코테 2021 강의] 2022.01.16
https://www.youtube.com/watch?v=2zjoKjt97vQ&list=PLRx0vPvlEmdAghTr5mXQxGpHjWqSz0dgC&index=2

1. 강의 듣고 문제 풀기 및 매주 백준 문제 풀기



## 코딩테스트

* 출력이 십만개 이상인 경우 bw를 이용해 관리하기!



### 시간복잡도

- 상수와 같은 값이라면 가장 큰 값으로 시간복잡도를 구함
  - 2 * 0(n) + 0(L) → 0(n)
- 코테를 볼 때는 같은 알고리즘이라도 시간복잡도가 작은 메소드를 사용해야 함.

```java
# 시간복잡도: 0(n) -> N 이 1000만인 경우
public static int getMaxInArray(int[] arr) {
	int maxValue = arr[0];
	for(int i = 1; i < arr.length; i++)
		if(arr[i] > maxValue) maxValue = arr[i];;
	return maxValue; 
}
```

```java
# 시간복잡도: 0(n2) -> 뭐라도 상관없다면!
public static int getMaxInArray(int[] arr) {
	Arrays.sort(arr);
	return arr[arr.length - 1]; 
}
```

| N의 범위                                         | 시간복잡도            |
| ------------------------------------------------ | --------------------- |
| N <= 10 ~ 11                                     | O(N!)                 |
| N <= 24 ~ 25                                     | O(2^N)                |
| N <= 300 ~ 500                                   | O(N^3)                |
| N <= 5,000 ~ 10,000                              | O(N^2)                |
| N <= 50,000 ~ 100,000                            | O(N√N)                |
| N <= 100,000 ~ 1,000,000                         | O(N log N)            |
| N <= 10,000,000                                  | O(N)                  |
| N개의 데이터가 입력이 아닌 범위 등으로 주어질 때 | O(√N), O(log N), O(1) |

* 1억 ~ 3억 에 최대 1초.

#### ASCII TABLE

| Decimal | Hex  | Char | Decimal | Hex  | Char |
| ------- | ---- | ---- | ------- | ---- | ---- |
| 65      | 41   | A    | 97      | 61   | a    |
| 66      | 42   | B    | 98      | 62   | b    |
| 67      | 43   | C    | 99      | 63   | c    |
| 68      | 44   | D    | 100     | 64   | d    |
| 69      | 45   | E    | 101     | 65   | e    |
| 70      | 46   | F    | 102     | 66   | f    |
| 71      | 47   | G    | 103     | 67   | g    |
| 72      | 48   | H    | 104     | 68   | h    |
| 73      | 49   | I    | 105     | 69   | i    |
| 74      | 4A   | J    | 106     | 6A   | j    |
| 75      | 4B   | K    | 107     | 6B   | k    |
| 76      | 4C   | L    | 108     | 6C   | l    |
| 77      | 4D   | M    | 109     | 6D   | m    |
| 78      | 4E   | N    | 110     | 6E   | n    |
| 79      | 4F   | O    | 111     | 6F   | o    |
| 80      | 50   | P    | 112     | 70   | p    |
| 81      | 51   | Q    | 113     | 71   | q    |
| 82      | 52   | R    | 114     | 72   | r    |
| 83      | 53   | S    | 115     | 73   | s    |
| 84      | 54   | T    | 116     | 74   | t    |
| 85      | 55   | U    | 117     | 75   | u    |
| 86      | 56   | V    | 118     | 76   | v    |
| 87      | 57   | W    | 119     | 77   | w    |
| 88      | 58   | X    | 120     | 78   | x    |
| 89      | 59   | Y    | 121     | 79   | y    |
| 90      | 5A   | Z    | 122     | 7A   | z    |



### 배열

- **append()**: 가장 뒤에 원소 삽입
- **insert(int idx, int val)**: 현재 idx 번째 원소의 앞에 원소 삽입



### 완전탐색

- 효율을 생각하지 않기 떄문에 문제의 크기가 작으면 유용
- 문제의 크기가 클수록 시간/공간복잡도가 늘어나 적용이 어려울 수 있음



### 정렬알고리즘

**N제곱 정렬 알고리즘**

- Bubble Sort
- Selection Sort
- Insertion Sort

**NlogN 정렬 알고리즘**

- Quick Sort
  - 면접에서 자주 나옴!
- Merge Sort
- Heap Sort

**그 외**

- Counting Sort
- Radix Sort
- Bucket Sort

**Primitive[] sort**

- 알고리즘: **Dual-Pivot Quick Sort**
- 평균 시간 복잡도: O(NlogN)
- 최악 시간 복잡도: O(N제곱)
- stable이 보장되지 않음: 같은 위상(숫자)을 가진 값이라면 어떤 순서라도 가능

**Object[] sort**

- 알고리즘: **Tim Sort**
- 평균 시간 복잡도: O(NlogN)
- 최악 시간 복잡도: O(NlogN)
- stable이 보장되지 않음: 같은 위상(숫자)을 가진 값이라면 입력 순서가 먼저인 것이 먼저.
- 무조건 Tim Sort 가 좋진 않음.

**Set<String> set = new HashSet<>();**

- 중복된 원소를 가지지 않는 Collection
- add, remove, contains(존재하면 true, 없으면 false)
  - O(1) ~ O(비교복잡도 * log(size)
- **HashSet**
  - **시간복잡도: O(1)**
  - 해시 테이블을 기반으로 한 unordered Collection
  - 삽입/삭제/조회 연산 : O(1) 기대. null 저장 가능
- **TreeSet**
  - **시간복잡도: O(logn)**
  - Binary Search Tree 를 기반으로 한 ordered Collection.
  - 순서를 가지는 연산
    - input: 6 5 1 2
    - output: 1 2 5 6
  - 삽입/삭제/조회 연산 : O(log(size) null 저장 불가

**LinkedList**

- 시간복잡도: O(1) ~ O(N)
  - sort: Collections.sort();

**ArrayList**

- insert(): 시간복잡도: O(N)
- remove(): 시간복잡도: O(N)
- add(): 시간복잡도: O(N)
  - sort: Collections.sort();
  - reverse: Collections.sert(list, Collections.reverseOrder());

**Integer**

- sort: Arrays.sort();
- reverse: Arrays.sort(list, Collections.reverseOrder());



### 구간합

- XOR 연산
  - 5, 3 이라는 수가 있다면 해당 수를 각각 2진수로 바꾸고 각 자리수마다 아래와 같은 연산을 해 나온 값을 구하는 연산.
  - 같은 값이면 0, 다른 값이면 1
  - 0 ^ 0 = 0
  - 0 ^ 1 = 1
  - 1 ^ 0 = 1
  - 1 ^ 1 = 0



### Binary Search

- 절반씩 계속 원하는 값이 나올때 까지 나눠서 답 구함!
- 시간복잡도: O(logN)
- Arrays에 binarySearch Method 존재!
- set으로도 풀고 binary search 로도 풀어서 시간 복잡도를 비교해보자!



### Parametric Search

- Binary Search 를 이용한 최적 값 탐색 기법
- 연속적이거나 이산적인 값의 집합에서 최적값 X를 찾는 문제에서
- X를 경계로 조건을 만족하는 집합과 답이 될 수 없는 집합을 판정할 수 있을 때
- 추정 값 A에 대한 판정을 반복해 X를 찾는 방법



### 투 포인터

* current Index : 현재까지 구한 Index 저장

1. [a b b] c a c c b a
   * c 까지 구했다나 N 보다 count 가 커졌기 때문에!
2. a [b b c] a c c b a
   * a까지 구했다나 N 보다 count 가 커졌기 때문에!



### 슬라이딩 윈도우

- 고정된 크기의 윈도우(범위)를 데이터 구조(배열 or 문자열)에서 한 칸씩 이동시키며 필요한 작업을 수행하는 기법

**슬라이딩 윈도우의 기본 개념**:

1. **윈도우 크기 설정**: 고정된 크기의 윈도우를 설정
2. **초기 윈도우 값 계산**: 배열의 첫 번째 위치부터 시작하여 윈도우의 값을 계산
3. **윈도우 이동**: 윈도우를 한 칸씩 이동하면서 새로운 값을 추가하고, 이전 값을 제거. 이 과정에서 윈도우 내 값들을 업데이트
