## 잃어버린 괄호

https://www.acmicpc.net/problem/1541

## 내 답안

* 첫번째 답안은 시간 초과로 실패....
* **이유**: 
  * 변수 선언해 '-' 일 경우 더해서 '+' 연산이 나올때 한번에 마이너스 되도록 코드 짬 (설명부터 복잡...!)

* 결과는 시간초과...!

  ![img](https://postfiles.pstatic.net/MjAyNTEwMjhfMTg2/MDAxNzYxNjU0OTI2ODIz.E4OXdZX9i2qo0i-PfO2xiWq5x798Psu06pJwROcgXR4g.ui-1pxvFZS5Qyc8RMuD19AIeMPeXpLMfE18-O_Qh1zUg.PNG/image.png?type=w773)

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String n = sc.next();

        String[] su = n.replaceAll("\\D", " ").split(" ");
        String[] operator = n.replaceAll("\\d", "").split("");

        int answer = Integer.parseInt(su[0]);
        int minus = 0;

        for(int i=0; i<operator.length; i++){
            if(operator[i].equals("+")){
                if(minus > 0){
                    minus += Integer.parseInt(su[i+1]);
                }else{
                    answer += Integer.parseInt(su[i+1]);
                }
            }else{
                answer -= minus;
                minus = 0;
                minus += Integer.parseInt(su[i+1]);
            }
        }

        if(minus > 0){
            answer -= minus;
        }

        System.out.println(answer);

    }

}
```

* 두번째 풀이의 경우: 

  * split 시 '-' 기준으로 나눔!
  * 결과적으로 복잡한 연산 없이 '+' 기준으로 연산하는 메소드를 `캡슐화` 해 시간초과 문제 해결

  ![img](https://postfiles.pstatic.net/MjAyNTEwMjhfMTU3/MDAxNzYxNjU0NTA5NDA3.-SN7Bban2e4Xi3PVh4MnmEohlik6Dw421N7CiMv8Kugg.5IA5HscEvcniDnAbfSON7tfJ7Ye58i7I-zndLEa6J6Mg.PNG/image.png?type=w773)

```java
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String n = sc.next();
        int answer = 0;

        String[] su = n.split("-");
        answer = plusOf(su[0]);

        for(int i=1; i<su.length; i++){
            answer -= plusOf(su[i]);
        }
        System.out.println(answer);

    }

    public static int plusOf(String s){
        String[] plusSu = s.split("\\+");
        int su = 0;
        for(int i=0; i<plusSu.length; i++){
            su+=Integer.parseInt(plusSu[i]);
        }
        return su;
    }

}
```



