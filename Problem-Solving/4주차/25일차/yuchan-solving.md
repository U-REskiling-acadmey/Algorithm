## 문제 풀이
```java
import java.util.*;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        
        int[] answer = new int[commands.length];

        for(int i=0;i<commands.length;i++){
            int first = commands[i][0]-1;
            int last = commands[i][1];

            int[] arr = Arrays.copyOfRange(array,first,last);
            Arrays.sort(arr);
            answer[i] = arr[commands[i][2]-1];
        }
        
        return answer;
    }
}
```

이번 문제는 도저히 어떻게 구현해야 될지 감을 잡지 못해서 검색의 힘을 빌렸다.  
copyOfRange라는 함수를 통해서 이렇게 배열을 불리할 있는 방법을 알게 되었다.

하지만 구지 라이브러리를 사용하지 않아도 이러한 문제를 해결할 수 있는 알고리즘 실력을 기르고 싶다.  
그렇기 때문에 앞으로는 라이브러리의 의존성을 줄이고 최대한 순수 알고리즘으로 구현하는 실력을 키워보려고 한다.

### 참고 문헌
- <a href="https://hianna.tistory.com/619">copyOfRange 사용법</a>