## 없는 수 더하기

문제에서 0부터 9까지의 숫자 중 일부가 들어 있는 numbers가 주어질 때  
없는 숫자의 합을 구하는 문제이다.

여기서 나는 numbers를 정렬하고 Arrays.binarySearch를 사용하여 배열에 특정  
숫자가 있는지 확인하는 조건을 만들어주어서 풀었습니다.

```java
import java.util.*;

class Solution {
    public int solution(int[] numbers) {
        int sum = 0;
        
        Arrays.sort(numbers);
        for (int i = 0; i <= 9; i++) {
            // binarySearch를 사용하여 숫자가 배열에 있는지 확인
            if (Arrays.binarySearch(numbers, i) < 0) {
                sum += i;
            }
        }
        
        return sum;
    }
}
```