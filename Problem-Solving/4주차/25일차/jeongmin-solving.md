## 코드

```java
import java.util.Arrays;

class Solution {
    public int[] solution(int[] array, int[][] commands) {
        int[] answer = new int[commands.length];

        for(int i = 0; i < commands.length; i++) {
            int first = commands[i][0] - 1;
            int end = commands[i][1];

            int[] arr = Arrays.copyOfRange(array, first, end);
            Arrays.sort(arr);
            answer[i] = arr[commands[i][2] - 1];
        }
        return answer;
    }
}
```

## 해설

commands 배열을 순회하면서 각 명령에 따라 array를 자르고 정렬한 후, 값을 answer에 저장한다. <br>

1. 각 명령에 따라 array의 일부를 copyOfRange로 잘라낸다.
2. 잘라낸 배열을 정렬한다.
3. 정렬된 배열에서 지정된 위치의 값을 answer 배열에 저장한다.
