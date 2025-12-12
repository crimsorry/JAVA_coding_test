# 보석쇼핑

https://school.programmers.co.kr/learn/courses/30/lessons/67258?gad_source=1&gad_campaignid=22499034228&gbraid=0AAAAAC_c4nB08qazVsiPysyNMaqqGnaBP&gclid=Cj0KCQiA9OnJBhD-ARIsAPV51xPrMsb0-sr0UkJ7a_gPwgyyGFd9p78HfgQ0sUbhyiUrgEhnfdSEeesaAgcgEALw_wcB

## 내 풀이

* 투포인터 + 슬라이딩 위도우 문제

```python
import java.util.*;

class Solution {
    public int[] solution(String[] gems) {
        Set<String> set = new HashSet<>(Arrays.asList(gems));
        Map<String, Integer> map = new HashMap<>();

        int left = 0;
        int right = 0;
        int minLen = Integer.MAX_VALUE;
        int[] answer = {1, gems.length};

        map.put(gems[0], 1);

        while (left <= right && right < gems.length) {
            if (map.size() == set.size()) {
                if (right - left < minLen) {
                    minLen = right - left;
                    answer[0] = left + 1;
                    answer[1] = right + 1;
                }

                map.put(gems[left], map.get(gems[left]) - 1);
                if (map.get(gems[left]) == 0) map.remove(gems[left]);
                left++;

            } else {
                right++;
                if (right < gems.length) {
                    map.put(gems[right], map.getOrDefault(gems[right], 0) + 1);
                }
            }
            System.out.println(map);
        }

        return answer;
    }
}
```



