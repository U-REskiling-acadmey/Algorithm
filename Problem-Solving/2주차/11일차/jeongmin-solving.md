## 코드

```java
import java.util.ArrayList;

public class Solution {
    public int[] solution(int []arr) {
        int temp = -1;

        //ArrayList에 값 저장
        ArrayList<Integer> list=new ArrayList<>();
        for(int n: arr) {
            if(n != temp) list.add(n);
            temp=n;
        }

        //ArrayList를 int배열로 변환
        int[] answer = new int[list.size()];
        for(int i=0; i<list.size(); i++) answer[i] = list.get(i);

        return answer;
    }
}
```

## 해설

연속된 중복을 없애야 함으로, arr를 돌면서 값을 temp에 저장하고 비교하는 방법으로 풀었습니다.
