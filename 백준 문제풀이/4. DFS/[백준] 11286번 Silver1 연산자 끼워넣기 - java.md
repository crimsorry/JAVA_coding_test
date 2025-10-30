# 연산자 끼워넣기

https://www.acmicpc.net/problem/14888

## 내 풀이

* **DFS**: 깊이우선탐색 사용

  1. **초기화**

     * minAnswer = Integer.MAX_VALUE

     * maxAnswer = Integer.MIN_VALUE

  2. 나눗셈 연산은 **C++ 기준**

  3. **순서 변경 X**

![img](https://postfiles.pstatic.net/MjAyNTEwMzBfMjI5/MDAxNzYxODI5NjUyOTY0.TZX1Ma51t7F8ewx6rOU0x8op2BSWYX5NUDlH58yfmd0g.WfaFSRSO566q4hd6xtepGS1O-EsrkxcOL2fdDllcuVQg.PNG/image.png?type=w773)

```java
import java.util.*;

public class Main {

    public static int minAnswer = Integer.MAX_VALUE;
    public static int maxAnswer = Integer.MIN_VALUE;
    public static int[] array;

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        array = new int[n];

        for(int i=0; i<n; i++){
            array[i] = sc.nextInt();
        }

        int[] operator = new int[4];

        for(int i=0; i<4; i++){
            operator[i] = sc.nextInt();
        }

        dfs(operator, array[0], 1);

        System.out.println(maxAnswer);
        System.out.println(minAnswer);
    }

    public static void dfs(int[] operator, int su, int chk){
        if(chk >= array.length){
            minAnswer = Math.min(minAnswer, su);
            maxAnswer = Math.max(maxAnswer, su);
            return;
        }

        for(int i=0; i<4; i++){
            if(operator[i] > 0){
                int next = su;
                switch (i) {
                    case 0:
                        next += array[chk];
                        break;
                    case 1:
                        next -= array[chk];
                        break;
                    case 2:
                        next *= array[chk];
                        break;
                    case 3:
                        if (next < 0)
                            next = - (Math.abs(next) / array[chk]);
                        else
                            next /= array[chk];
                        break;
                }
                operator[i]--;
                dfs(operator, next, chk+1);
                operator[i]++;
            }
        }
    }

}
```

