# 주차 요금 계산

https://school.programmers.co.kr/learn/courses/30/lessons/92341



## 내 풀이

```java
import java.util.*;

class Solution {
    public int[] solution(int[] fees, String[] records) {
        int baseTime = fees[0];
        int baseFee = fees[1];
        int unitTime = fees[2];
        int unitFee = fees[3];

        Map<String, Integer> inMap = new HashMap<>();     
        Map<String, Integer> totalMap = new HashMap<>(); 

        for (String record : records) {
            String[] r = record.split(" ");
            int time = toMinute(r[0]);
            String car = r[1];
            String type = r[2];

            if (type.equals("IN")) {
                inMap.put(car, time);
            } else {
                int inTime = inMap.remove(car);
                totalMap.put(car, totalMap.getOrDefault(car, 0) + (time - inTime));
            }
        }

        int end = toMinute("23:59");
        for (String car : inMap.keySet()) {
            int inTime = inMap.get(car);
            totalMap.put(car, totalMap.getOrDefault(car, 0) + (end - inTime));
        }

        // 차량 번호 정렬
        List<String> cars = new ArrayList<>(totalMap.keySet());
        Collections.sort(cars);

        int[] answer = new int[cars.size()];
        for (int i = 0; i < cars.size(); i++) {
            int time = totalMap.get(cars.get(i));
            int fee = baseFee;
            if (time > baseTime) {
                fee += Math.ceil((time - baseTime) / (double) unitTime) * unitFee;
            }
            answer[i] = fee;
        }

        return answer;
    }

    private int toMinute(String time) {
        String[] t = time.split(":");
        return Integer.parseInt(t[0]) * 60 + Integer.parseInt(t[1]);
    }
}
```



