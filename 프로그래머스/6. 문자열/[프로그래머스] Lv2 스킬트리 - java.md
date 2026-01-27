# 스킬트리

https://school.programmers.co.kr/learn/courses/30/lessons/49993



## 내 풀이

```python
class Solution {
    public int solution(String skill, String[] skill_trees) {
        int answer = 0;
        
        for(String tree : skill_trees){
            int chk = 0;
            for(char t : tree.toCharArray()){
                if(skill.indexOf(t) > chk){
                    chk = -1;
                    break;
                }else if(skill.indexOf(t) == chk){
                    chk++;
                }
            }
            if(chk >= 0) answer++;
        }
        
        return answer;
    }
}
```



