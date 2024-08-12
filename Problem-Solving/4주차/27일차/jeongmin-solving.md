## 코드

```java
import java.util.Arrays;

class Solution {
    public int solution(int k, int m, int[] score) {
        int answer = 0;

        Arrays.sort(score);
        for(int i=score.length-m; i>=0; i-=m) {
            answer += score[i]*m;
        }

        return answer;
    }
}
```

## 해설

박스 1개에 m개의 사과가 있고, 가장 낮은 점수의 사과로 가격이 결정된다<br>
높은 점수의 사과들을 모아 박스를 만들고 그중 가장 작은 수가 값이 된다.<br>
<br>

1. score를 오름차순으로 정렬한다.
2. score.length에서 m을 값을 i의 시작값으로하고 m을 빼면서 for를 순회한다.<br>
3. score[i]값은 한 상자에서 가장 작은 값이 된다. 그러므로 answer에 `score[i]*m`(한 상자값)을 누적하여 답을 구한다.
