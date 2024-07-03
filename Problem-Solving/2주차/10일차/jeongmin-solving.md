## 코드

```java
import java.util.HashSet;

class Solution {
    public int solution(int[] nums) {
        int answer = 0;
        int max = nums.length/2;

        HashSet<Integer> set = new HashSet<>();
        for (int n: nums) set.add(n);

        answer = max < set.size() ? max : set.size();
        return answer;
    }
}
```

## 해설

hashset을 통해 중복을 제거한 후 set사이즈와 가져갈 수 있는 최대수와 비교하여 구했습니다.
