# 순위검색

https://school.programmers.co.kr/learn/courses/30/lessons/72412



## 내 풀이

```python
import java.util.*;
import java.util.stream.Collectors;

class Solution {
    public static HashMap<String, ArrayList<Integer>> map = new HashMap<>();

    public int[] solution(String[] info, String[] query) {
        int[] answer = new int[query.length];

        for (String inf : info) {
            String[] parts = inf.split(" ");
            String lang = parts[0];
            String job = parts[1];
            String career = parts[2];
            String food = parts[3];
            int score = Integer.parseInt(parts[4]);

            makeKeys(new String[]{lang, job, career, food}, 0, "", score);
        }

        for (String key : map.keySet()) {
            Collections.sort(map.get(key));
        }

        for (int i = 0; i < query.length; i++) {
            String q = query[i].replaceAll(" and ", " ");
            String[] qParts = q.split(" ");
            String key = qParts[0] + qParts[1] + qParts[2] + qParts[3];
            int scoreReq = Integer.parseInt(qParts[4]);

            if (map.containsKey(key)) {
                List<Integer> scores = map.get(key);
                int idx = lowerBound(scores, scoreReq);
                answer[i] = scores.size() - idx;
            } else {
                answer[i] = 0;
            }
        }

        return answer;
    }

    private void makeKeys(String[] arr, int depth, String curr, int score) {
        if (depth == arr.length) {
            map.computeIfAbsent(curr, k -> new ArrayList<>()).add(score);
            return;
        }
        makeKeys(arr, depth + 1, curr + arr[depth], score);
        makeKeys(arr, depth + 1, curr + "-", score);
    }

    private int lowerBound(List<Integer> list, int target) {
        int left = 0;
        int right = list.size();

        while (left < right) {
            int mid = (left + right) / 2;
            if (list.get(mid) >= target) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return left;
    }
}

```



