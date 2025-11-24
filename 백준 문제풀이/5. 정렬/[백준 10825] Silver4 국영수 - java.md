## 국영수

https://www.acmicpc.net/problem/10825

## 내 풀이

* ArrayList 활용
* Collections.sort 활용

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.Scanner;

public class Main {

    public static class Score{
        String name;
        int kor;
        int eng;
        int math;

        public Score(String name, int kor, int eng, int math){
            this.name = name;
            this.kor = kor;
            this.eng = eng;
            this.math = math;
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        StringBuilder sb = new StringBuilder();

        int n = sc.nextInt();
        ArrayList<Score> score = new ArrayList<>();

        for(int i=0; i<n; i++){
            score.add(new Score(sc.next(), sc.nextInt(), sc.nextInt(), sc.nextInt()));
        }

        Collections.sort(score, (s1, s2) -> {
            if(s1.kor!=s2.kor){
                return s2.kor - s1.kor;
            }
            if(s1.eng!=s2.eng){
                return s1.eng - s2.eng;
            }
            if(s1.math!=s2.math){
                return s2.math - s1.math;
            }
           return s1.name.compareTo(s2.name);
        });

        for(Score s : score){
            sb.append(s.name + "\n");
        }

        System.out.println(sb);

    }
}

```
