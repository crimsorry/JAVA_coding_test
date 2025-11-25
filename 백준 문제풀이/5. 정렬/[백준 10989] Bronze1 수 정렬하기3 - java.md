# 수 정렬하기3

https://www.acmicpc.net/problem/10989

## 내 풀이

* BufferedReader 활용
* BufferedWrite 활용

```java
import java.io.*;

public class Main {

    public static void main(String[] args) throws IOException {

        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));

        int modular = 10_001;
        int n = Integer.parseInt(br.readLine());
        int[] arr = new int[modular];

        for(int i=0; i<n; i++){
            int su = Integer.parseInt(br.readLine());
            arr[su]++;
        }

        for(int i=1; i<modular; i++){
            for(int j=0; j<arr[i]; j++){
                bw.write(i + "\n");
            }
        }

        bw.flush();

    }

}

```
