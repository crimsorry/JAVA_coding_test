## 나이순 정렬

https://www.acmicpc.net/problem/10814

## 내 풀이

* ArrayList 활용
* Collections.sort 활용

```java
import java.util.*;

public class Main {

    public static class User{
        int age;
        String name;

        public User(int age, String name){
            this.age = age;
            this.name = name;
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int[] age = new int[n];
        ArrayList<User> user = new ArrayList<>();


        for(int i=0; i<n; i++){
            user.add(new User(sc.nextInt(), sc.next()));
        }

        Collections.sort(user, (u1, u2) -> {
            return u1.age - u2.age;
        });

        for(User u : user){
            System.out.println(u.age + " " + u.name);
        }

    }

}

```
