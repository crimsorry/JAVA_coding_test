## 팰린드롬 만들기

https://www.acmicpc.net/problem/1213

## 내 풀이

* HashMap 을 이용하여 각 문자열의 갯수 구하기
* ArrayList 에 key값을 세팅하여 left, right 값 출력!

![image-20251101230340159](C:\Users\user\AppData\Roaming\Typora\typora-user-images\image-20251101230340159.png)

```python
import java.util.*;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String n = sc.next();

        HashMap<Character, Integer> hm = new HashMap<>();

        for(int i=0; i<n.length(); i++){
            Character c = n.charAt(i);
            hm.put(c, hm.getOrDefault(c, 0) + 1);
        }

        ArrayList<Character> arr = new ArrayList<>(hm.keySet());

        Collections.sort(arr);

        StringBuilder sb = new StringBuilder();
        int oddCnt = 0;
        Character odd = null;

        for(int i=0; i<arr.size(); i++){
            if(hm.get(arr.get(i))%2==1){
                oddCnt++;
                odd = arr.get(i);
            }
            for(int j=0; j<hm.get(arr.get(i))/2; j++){
                sb.append(arr.get(i));
            }
        }

        if(oddCnt>1){
            System.out.println("I'm Sorry Hansoo");
            return;
        }else if(oddCnt==1){
            sb.append(odd);
        }

        for(int i=arr.size()-1; i>=0; i--){
            for(int j=0; j<hm.get(arr.get(i))/2; j++){
                sb.append(arr.get(i));
            }
        }

        System.out.println(sb);

    }

}

```

