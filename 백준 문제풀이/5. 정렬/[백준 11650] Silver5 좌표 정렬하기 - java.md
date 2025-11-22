## 좌표 정렬하기

https://www.acmicpc.net/problem/11650

## 내 풀이

* 2차원 배열 Arrays.sort() 정렬 사용
* 람다식 사용
* System.out.println() (싱글톤)
  * 반복문 마다 sout 하게 되면 매 호출마다 OS I/O(system call) 일으킴
  * 따라서 StringBuilder 사용 하여 한번에 sout

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        StringBuilder sb = new StringBuilder();

        int n = sc.nextInt();
        int[][] arr = new int[n][2];

        for(int i=0; i<n; i++){
            arr[i][0] = sc.nextInt();
            arr[i][1] = sc.nextInt();
        }

        Arrays.sort(arr, (s, e) -> {
                    if(s[0] == e[0]){
                        return Integer.compare(s[1], e[1]);
                    }
                    return Integer.compare(s[0], e[0]);
                }
            );

        for(int i=0; i<n; i++){
            sb.append(arr[i][0] + " " + arr[i][1] + "\n");
        }

        System.out.println(sb);
    }

}

```
