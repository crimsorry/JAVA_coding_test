## ATM

https://www.acmicpc.net/problem/11399

## 내 풀이

![img](https://private-user-images.githubusercontent.com/31988854/508871791-edf61995-b916-48c4-abd3-576aabf66812.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NjIxNjE3OTEsIm5iZiI6MTc2MjE2MTQ5MSwicGF0aCI6Ii8zMTk4ODg1NC81MDg4NzE3OTEtZWRmNjE5OTUtYjkxNi00OGM0LWFiZDMtNTc2YWFiZjY2ODEyLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTExMDMlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUxMTAzVDA5MTgxMVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWNjYzBlYWM2OGQxMTAwZjYwNTU3N2E0YzVlYWIxM2I0NzEzNzRkNWM4N2M2ZmIyYzE4ZWZkZWIwYmYyZWI2MmYmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.lZ0r3Wa6pVNfsKeDWZMLbjChG6MIuhiKP40jSR7w4a8)

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();
        int[] array = new int[n];

        for(int i=0; i<n; i++){
            array[i] = sc.nextInt();
        }

        Arrays.sort(array);
        int answer = array[0];

        for(int i=1; i<n; i++){
            array[i] = array[i] + array[i-1];
            answer += array[i];
        }

        System.out.println(answer);


    }

}

```

