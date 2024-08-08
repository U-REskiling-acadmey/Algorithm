## 문제 풀이
```java
import java.util.*;

class Solution {
    public String solution(String[] participant, String[] completion) {
        String incompleteParticipant = findIncompleteParticipant(participant, completion);
        return incompleteParticipant;
    }
    
    public static String findIncompleteParticipant(String[] participant, String[] completion) {
        // HashMap을 사용하여 참가자와 완주자를 관리
        HashMap<String, Integer> map = new HashMap<>();

        // 참가자 리스트를 HashMap에 저장
        for (String part : participant) {
            map.put(part, map.getOrDefault(part, 0) + 1);
        }

        // 완주자 리스트를 HashMap에서 제거
        for (String comp : completion) {
            map.put(comp, map.get(comp) - 1);
        }

        // 완주하지 못한 참가자 찾기
        for (String key : map.keySet()) {
            if (map.get(key) != 0) {
                return key; // 완주하지 못한 참가자 반환
            }
        }
        return null; // 모든 참가자가 완주한 경우 null 반환 (이 경우는 발생하지 않음)
    }
}
```