## 코드

```java
import java.util.HashMap;

class Solution {
    public String solution(String[] participant, String[] completion) {
        HashMap<String, Integer> map = new HashMap<>();

        for (String name: participant) {
            map.put(name, map.getOrDefault(name, 0) + 1);
        }

        for (String name: completion) {
            map.put(name, map.get(name) - 1);
        }

        for (String name: map.keySet()) {
            if (map.get(name) == 1) {
                return name;
            }
        }

        return "";
    }
}
```

## 해설

완주하지 못한 한사람을 찾아야 한다.<br>
hashmap를 사용해서 출전선수를 모두 카운트 한다<br>
이후 완주한 선수들을 각각 카운트에서 -1 해준다<br>
그러면 카운트가 1인 사람이 정답이 된다.
