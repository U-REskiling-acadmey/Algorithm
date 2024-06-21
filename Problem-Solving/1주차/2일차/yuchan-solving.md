## 작성 코드
```java
import java.util.*;

public class Solution {
    public int solution(int n) {
        int sum = 0;

        while (n>0){
            sum += n%10;
            n/=10;
        }
        
        return sum;
    }
}
```

이번 문제는 각각의 자릿수를 구하는 문제였습니다. 숫자를 10으로 반복해서 나눠가면서  
10으로 나머지 연산을 하면 일의 자리를 얻을 수 있습니다.