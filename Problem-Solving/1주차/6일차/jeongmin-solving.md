## 코드

```java
import java.util.Stack;

class Solution {
    public int solution(int[] ingredient) {
        int answer = 0;
        Stack<Integer> st = new Stack<>();

        for (int i: ingredient) {
            st.push(i);
            if(st.size() >= 4) {
                int n = st.size();
                if (st.get(n-1) == 1 && st.get(n-2) == 3 && st.get(n-3) == 2 && st.get(n-4) == 1){
                    for (int j=0; j<4; j++) {
                        st.pop();
                    }
                    answer++;
                }
            }
        }
        return answer;
    }
}
```

## 해설

재료들을 stack에 넣으면서 사이즈가 4이상일때 1,2,3,1 이 맞는지 확인 후 그 값들을 지워주고 수를 카운트하였습니다.
