## 코드

```java
import java.util.HashMap;
import java.util.Map;

class Solution {
    public String[] solution(String[] players, String[] callings) {
        Map<String, Integer> playersMap = new HashMap<>();
        // 빠른검색을 위해 map에 저장
        for (int i = 0; i < players.length; i++) {
            playersMap.put(players[i], i);
        }

        for(String name: callings){
            int idx = playersMap.get(name);
            String front = players[idx - 1];
            // 순위 변경
            players[idx - 1] = name;
            players[idx] = front;
            // map에 업데이트
            playersMap.put(name, idx - 1);
            playersMap.put(front, idx);
        }

        return players;
    }
}

```

## 해설

hashmap을 사용하지 않았을때 런타임에러가 발생하였습니다.
배열 callings을 순회하면서 선수들의 순위를 변경하여 구합니다.
