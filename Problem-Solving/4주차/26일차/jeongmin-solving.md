## 코드

```java
import java.util.Set;
import java.util.TreeSet;

class Solution {
    public Set<Integer> solution(int[] numbers) {
        Set<Integer> set = new TreeSet<>();

        for (int i=0; i<numbers.length; i++) {
            for (int j=i+1; j<numbers.length; j++) {
                set.add(numbers[i] + numbers[j]);
            }
        }

        return set;
    }
}
```

## 해설

numbers배열의 두수로 만들 수 있는 모든 수의 배열에서 중복되지 않고 정렬해야된다.<br>
TreeSet을 이용하여 중복되지 않게하였고 자동 정렬되게한다.<br>
2중 for로 만들 수 있는 모든 수를 set에 넣으면 된다.
