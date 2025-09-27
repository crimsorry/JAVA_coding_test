## [2025 코테 공부] 2025.08.31 ~

#### 목표

1. 매일 1일 1코테를 진행하기
2. 내가 푼 코드 복습하면서 잊지 않도록 노력하기

## [2024 코딩테스트 스터디] 2024.12.10 ~ 2025.03.06

## [2021 이코테 강의] 2022.01.16

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
- **LinkedHashSet**
  - **시간복잡도: O(1)** (HashSet과 거의 동일)
  - 순서 O
  - 해시 테이블 + 이중 연결 리스트 구조
  - `add`, `contains`, `remove` → O(1) (HashSet과 거의 동일)
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
<<<<<<< HEAD



### 그래프

**방향 그래프**

```java
A ---> B (out degree)
A <--- C (in degree) 
```

- 간선에 방향이 있는 그래프
- A > B 로 향하는 간선과, B > A 로 향하는 간선이 서로 다를 수 있다.

**무방향 그래프**

```java
A ---- B
```

- 간선에 방향이 없는 그래프
- A-B 를 연결하는 간선이 동일한 간선

**정점의 차수(Degree)**

- 정점에 연결된 간선의 수
- 무방향 그래프: 정점의 차수와 간선의 수가 같음
- 방향 그래프: 진입차수(in degree) 진출차수(out degree) 로 나눠짐

**경로**

- 점점을 연결된 간선을 따라 탐색하는 순서대로 나타낸 것

**사이클**

- 간선의 경로 중 시작 정점과 끝 정점이 동일한 경로
- 사이클이 없는 그래프: 트리

**가중치 그래프**

```java
A --(3)--> B (비용 작성!)
```

- 간선에 가중치 혹은 비용이 할당된 그래프
- 연결된 정점들 간 탐색에 드는 비용이나, 연결강도 등을 표현함
- 구현 시 **객체(클래스) 로 묶어서 표현**하면 `가독성 좋은 코드`를 작성할 수 있다.

```java
class Node{
	int node; 정점
	int cost; 간선
	
	public Node(int node, int dist){
		this.node = node;
		this.dist = dist;
	}
}
```

**인접 행렬**

- test[행][열] = 연결여부(or 가중치)
- 공간복잡도
  - V개의 정점이 있다면, `V*V`만큼의 공간을 사용
- 시간 복잡도
  - 연결관계(가중치) 조회/저장: `O(1)` (단일)
  - 정점에 연결된 모든 간선 조회: `O(V)` (모든 간선) < V 만큼 선형 탐색 필요.

**인접 리스트 (메모리 다운!)**

- 장점의 정보: 배열
- 간선의 정보: 리스트 {가중치 + 정점}
- graph[행] = new ArrayList<Node>()
  - 정점별로 간선의 정보를 저장하는 리스트 만듬
- 공간 복잡도
  - V개의 정점, E개의 간선이 있다면 `V+E`만큼 공간 사용 **(간선 그래프가 작을수록 유리!)**
- 시간 복잡도
  - 연결관계(가중치) 조회/저장: `O(Outdegree(V))` (단일)
  - 정점에 연결된 모든 간선 조회: `O(Outdegree(V))` (모든 간선)



### Queue

- 뒤에 원소를 삽입하고, 앞에 원소를 제거할 수 있는 Queue
  - Queue<Integer> q = new LinkedList<>();
  - `add()`: 원소를 큐에 추가, 큐에 공간이 없다면 Exception 발생
  - `offer()`: 원소를 큐에 추가, 큐에 공간이 없다면 false 반환
  - `remove()`: 큐의 head 원소를 제거하고 반환, 큐가 비었다면 Exception 발생
  - `poll()`: 큐의 head 원소를 제거하고 반환. 큐가 비없다면 null 반환
  - `element()`: 큐의 head 원소 반환, 큐가 비없다면 Exception 발생
  - `peek()`: 큐의 head 원소 반환, 큐가 비었다면 null 반환
  - 선언: Queue<Integer> q = new LinkedList<>();
  
  ```
  offer > 1
  offer > 1, 2
  offer > 1, 2, 3
  
  pull > 2, 3
  pull > 3
  ```
  
  

### Deque

- 양쪽 끝에 원소를 삽입/제거할 수 있는 양방향 Queue
- Deque<Integer> s = new LinkedList<>();
- `offerFirst()`: 원소를 head 에 추가
- `offerLast()`: 원소를 마지막에 추가
- `pollFirst()`: 큐의 head 제거하고 반환
- `pollLast()`: 큐의 마지막 제거하고 반환
- `peekFirst()`: 큐의 head 원소 반환
- `peekLast()`: 큐의 마지막 원소 반환

```
offerFirst > 1
offerFirst > 2, 1
offerFirst > 3, 2, 1

pullFirst > 2, 1
pullFirst > 1

offerLast > 1
offerLast > 1, 2
offerLast > 1, 2, 3

pullLast > 1, 2
pullLast > 1
```



### Stack

- 마지막에 넣은 데이터가 먼저 나오는 후입선출 자료구조(Last-In First-Out)
- Deque<Integer> s = new ArrayDeque<>();
  - LinkedList 와 ArrayDeque 차이점
    - **성능**: `ArrayDeque`는 대부분의 경우에서 더 빠른 성능을 제공. 특히, 삽입 및 삭제가 빈번하게 일어날 때와 순차 접근이 필요할 때 유리.
    - **메모리 사용**: `ArrayDeque`는 메모리를 더 효율적으로 사용할 수 있음.
    - **특정 상황에서의 유용성**: `LinkedList`는 삽입과 삭제가 리스트의 중간에서 자주 일어나는 경우 유리. 그러나 `ArrayDeque`는 일반적인 스택과 큐 작업에서 더 나은 성능을 제공.
- `offerFirst()`: 원소를 head 에 추가
- `pollFirst()`: 큐의 head 제거하고 반환
- `peekFirst()`: 큐의 head 원소 반환
  -  Stack 은 앞쪽에서 연산이 일어날 수 있기 때문에 보다 직관적인 First 메소드 사용!

- 단일 스레드 환경에서 훨씬 빠름!

```
offerFirst > 1
offerFitst > 2, 1
offerFirst > 3, 2, 1

pullFirst > 2, 1
pullFirst > 1
```

* Stack<Integer> stack = new Stack<>();

  - `push(E item)` : top에 원소 추가

  - `pop()` : top 원소 꺼내서 반환 + 제거

  - `peek()` : top 원소 반환 (제거 ❌)

  - `empty()` : 비었는지 확인

  - 레거시. Stack 보다 Deque 가 성능 up
    - 자바 공식 문서에서도 `Deque` 쓰라고 명시 https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Stack.html



### BFS 와 DFS

**BFS (Breadth-First Search)**

- 넓이 우선 탐색
- `Queue` 를 이용하여 구현
- 탐색할 정점을 Queue 에 넣고
- **처음 방문하는 정점이 `큐에서 빠질때` 마다**

**DFS (Depth-First Search)**

- 깊이 우선 탐색
- `스택` or `재귀함수` 로 구현
- **처음 방문하는 정점이 `재귀에 진입`할 때 마다**



### 에라토스테네스의 체

소수 찾는 효율적인 방법

1. 1은 소수가 아니므로 제외
2. 가장 작은 소수 2 선택 후 2의 배수 지우기
3. 다음으로 작은 소수 3 선택 후 3의 배수 지우기
4. 그 다음 남아있는 작은 수(5) 선택 후 5의 배수 지우기
5. 이렇게 반복하면 남아있는 수는 모두 소수!
