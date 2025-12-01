## ROT13

https://www.acmicpc.net/problem/11655

## 내 풀이

```python
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        StringBuilder sb = new StringBuilder();

        String line = sc.nextLine();

        for(int i=0; i<line.length(); i++){
            char c = line.charAt(i);
            if(c >= 'A' && c <= 'Z'){
                c = (char) (((c - 'A' + 13) % 26) + 'A');
            }else if(c >= 'a' && c <= 'z'){
                c = (char) (((c - 'a' + 13) % 26 ) + 'a');
            }
            sb.append(c);
        }

        System.out.println(sb);

    }
}

```

