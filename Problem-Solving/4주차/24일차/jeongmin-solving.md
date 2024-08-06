## 코드

```java
import java.util.Arrays;

class Solution {
    public int solution(int[] d, int budget) {
        int answer = 0;
        Arrays.sort(d);
        for(int i=0; i<d.length; i++){
            budget -= d[i];
            if(budget < 0) break;
            answer++;
        }
        return answer;
    }
}
```

## 해설

최대한 많은 부서에 지원을 해야된다. <br>
작은 예산부터 지원해야 최대한 많은 부서를 지원하므로 <br>
d 를 오름차순으로 정렬하여 각 신청한 금액을 budget에서 빼주면서 answer를 +1 해준다<br>
여기서 +1 해주기 전에 budget값이 0보다 작으면 지원할 수 없으므로 break를 해준다.
