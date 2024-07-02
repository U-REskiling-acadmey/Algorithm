## 코드

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Collections;

class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        List<Integer> lostList = new ArrayList<>();
        List<Integer> reserveList = new ArrayList<>();
        for (int v : lost) lostList.add(v);
        for (int v : reserve) reserveList.add(v);

        // 체육복을 도난당했지만 여분이있는 학생 삭제
        for (int i=0; i<lost.length; i++) {
            int num = lost[i];
            if (reserveList.contains(num)) {
                lostList.remove(Integer.valueOf(num));
                reserveList.remove(Integer.valueOf(num));
            }
        }

        // 정렬이 안 되있을 수 있으므로 정렬
        Collections.sort(lostList);
        Collections.sort(reserveList);

        // 체육복을 나눠주기 전 수업에 참가가능한 학생 수
        int answer = n-lostList.size();

        // 잃어버린 학생의 앞뒤로 살펴보면서 체육복이 있으면 나눠줌
        for(int num: lostList){
            if(reserveList.contains(num-1)){
                answer++;
                reserveList.remove(Integer.valueOf(num-1));
            }else if(reserveList.contains(num+1)){
                answer++;
                reserveList.remove(Integer.valueOf(num+1));
            }
        }

        return answer;
    }
}
```

## 해설

코드에 주석으로 첨부

문제를 자세히 읽자. 정렬이 되있다고 생각해서 헤멨음.
