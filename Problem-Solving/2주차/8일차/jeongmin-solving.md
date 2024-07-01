## 코드

```java
import java.util.Comparator;
import java.util.Arrays;

class Solution {
    public int solution(int[][] sizes) {
        int len = sizes.length;
        int[] Warr = new int[len];
        int[] Harr = new int[len];

        for(int i=0; i<len; i++){
            if(sizes[i][0] < sizes[i][1]){
                int temp = sizes[i][0];
                sizes[i][0] = sizes[i][1];
                sizes[i][1] = temp;
            }
            Warr[i] = (sizes[i][0]);
            Harr[i] = (sizes[i][1]);
        }

        int W = Arrays.stream(Warr).max().getAsInt();
        int H = Arrays.stream(Harr).max().getAsInt();

        return W*H;
    }
}
```

## 해설

가로와 세로 길이에서 둘중 큰길이를 가로로 바꿔주고 각각 가로와 세로의 배열을 나눈다<br/>
나눈 배열들의 max값을 곱하였습니다.
