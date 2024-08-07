## 문제 풀이
```java
import java.util.*;

class Solution {
    public int solution(int[] d, int budget) {
        int answer = 0;
        int total = 0;

        Arrays.sort(d);//오름차순 정렬

        for(int i=0;i<d.length; i++){
            if(total+d[i]<=budget) {
                total += d[i]; //배열의 값을 하나 씩 더한다
                answer++;
            }
        }
        return answer;
    }
}
```
최대한 많은 부서의 물품을 구매해 주려고 하기 때문에, 먼저 배열을 오름차순으로 정렬한다. total이 budget값을   
넘기기 전까지 배열의 값을 더한 후 카운트를 증가시킨다.