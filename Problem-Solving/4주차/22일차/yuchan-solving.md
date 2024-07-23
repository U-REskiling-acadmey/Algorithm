## 문제 풀이
```java
import java.util.*;

class Solution {
    public int solution(int[] absolutes, boolean[] signs) {
        for(int i=0;i<absolutes.length;i++){
            if(!signs[i]) absolutes[i] = absolutes[i] * -1;
        }

        return Arrays.stream(absolutes).sum();
        
    }
}
```

이번 문제는 signs의 i번째 값이 false이면 absolutes의 i번째 값을 -1을 곱해주어서
최종적으로 더해주는 값을 반환하는 문제였습니다.

그래서 저는 조건문을 통해 signs를 불리하고 Arrays.stream을 통해 더해주었습니다.