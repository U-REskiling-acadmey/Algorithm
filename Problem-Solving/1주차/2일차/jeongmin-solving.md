## 코드

```java
import java.util.*;

public class Solution {
    public int solution(int N) {
        int answer = 0;

        while(N != 0){
            answer += N%10;
            N /= 10;
        }

        return answer;
    }
}
```

## 해설

주어진 자연수 N을 `N%10`을 하여 일의 자리수를 구한 후 answer에 더해주고,
`N/=10`을 하여 앞서 더한 일의 자리수를 소거합니다.

위의 방식을 while을 사용하여 N이 0이 될때까지 실행하여 각 자리수의 합을 구합니다.
