## [프로그래머스] : K번째수



## 문제 

H-Index는 과학자의 생산성과 영향력을 나타내는 지표입니다. 어느 과학자의 H-Index를 나타내는 값인 h를 구하려고 합니다. 위키백과[1](https://school.programmers.co.kr/learn/courses/30/lessons/42747#fn1)에 따르면, H-Index는 다음과 같이 구합니다.

어떤 과학자가 발표한 논문 `n`편 중, `h`번 이상 인용된 논문이 `h`편 이상이고 나머지 논문이 h번 이하 인용되었다면 `h`의 최댓값이 이 과학자의 H-Index입니다.

어떤 과학자가 발표한 논문의 인용 횟수를 담은 배열 citations가 매개변수로 주어질 때, 이 과학자의 H-Index를 return 하도록 solution 함수를 작성해주세요.



## 제한사항

- 과학자가 발표한 논문의 수는 1편 이상 1,000편 이하입니다.
- 논문별 인용 횟수는 0회 이상 10,000회 이하입니다.



## 입출력 예

| citations       | return |
| --------------- | ------ |
| [3, 0, 6, 1, 5] | 3      |



## 입출력 예 설명

이 과학자가 발표한 논문의 수는 5편이고, 그중 3편의 논문은 3회 이상 인용되었습니다. 그리고 나머지 2편의 논문은 3회 이하 인용되었기 때문에 이 과학자의 H-Index는 3입니다.



## 내 풀이

```java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        int answer = 0;
		
		Integer[] copy = Arrays.stream(citations).boxed().toArray(Integer[]::new);
		
		Arrays.sort(copy, Collections.reverseOrder());
		
		while(answer < citations.length) {
			if(copy[answer]<=answer) {
				break;
			}
			answer++;
		}
		
		return answer;
    }
}
```

> 1. int[] -> Integer[] 형변환
> 2. 역정렬
> 3. citations 길이만큼 while문 실행
> 4. answer 보다 copy[answer] 값이 더 작거나 같으면 break!



## 해맨 부분

> 1. 처음 코드를 실행했을때 테스트 케이스 1개가 실패를 해 계속 오류가 남.
>
>    {5, 5, 5, 5, 5} 같은 경우에 잘못된 정답이 나와서 코드 수정.
>
>    예외처리 더 생각하면서 코딩하기!