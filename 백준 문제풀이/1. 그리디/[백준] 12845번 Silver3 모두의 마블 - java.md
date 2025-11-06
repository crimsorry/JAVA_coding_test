## 동전0

https://www.acmicpc.net/problem/12845

## 내 답안

* 오름차숨 정렬 후 합계 구하기

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        Integer[] card = new Integer[n];

        for(int i=0; i<n; i++){
            card[i] = sc.nextInt();
        }

        Arrays.sort(card, Comparator.reverseOrder());

        int answer = 0;
        int last = card[0];

        for(int i=1; i<n; i++){
            answer = answer + last + card[i];
            last = Math.max(last, card[i]);
        }

        System.out.println(answer);
    }
}
```



