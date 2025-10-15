# 1로 만들기

https://www.acmicpc.net/problem/1463

## 내 풀이

* n 보다 작은 수. 1, 2, 3, ... n 일 때의 횟수 저장하기!

![img](https://postfiles.pstatic.net/MjAyNTEwMTVfNDkg/MDAxNzYwNTIwMDQyMDUz.Hu3MdcS7buYs6QTM00RyCxZI6rwz8B6DMpW0jcgD8rEg.Sh6xosAhDVe8DnqWOSNmT1S6pNKCyrFKrVm1biD7uCgg.PNG/image.png?type=w773)

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] array = new int[n+1]; // n 이 1, 2, 3 ... 10 인 경우의 (i 번째) 횟수 (value) 저장!
        array[1] = 0;

        for(int i=2; i<=n; i++){
            array[i] = array[i-1] + 1; // 일단 1을 뺀 경우 > 1을 뺀 n 의 횟수 보다 + 1!
            if(i % 2 == 0) {
                array[i] = Math.min(array[i], array[i / 2] + 1); // 직전 2 나눈 횟수 보다 + 1!
            }
            if(i % 3 == 0){
                array[i] = Math.min(array[i], array[i / 3] + 1); // 직전 3 나눈 횟수 보다 + 1!
            }
        }

        System.out.println(array[n]);

    }

}
```

