## 작성코드
```java
import java.util.*;

class Solution {
    public int solution(String s) {
        int count = 0;

        String[] list = s.split("");
        List<String> charList = new ArrayList<>(Arrays.asList(list));

        while (!charList.isEmpty()) {
            String firstChar = charList.get(0);
            int cnt1 = 0, cnt2=0;
            int i;
            for (i = 0; i < charList.size(); i++) {
                if (firstChar.equals(charList.get(i))) {
                    cnt1++;
                } else cnt2++;
                if(cnt1 == cnt2) break;
            }
            count++;

            int removeCount = Math.min(i + 1, charList.size());
            for (int j = 0; j < removeCount; j++) charList.remove(0);
        }
        return count;
    }
}
```

## 해설
1. 입력 문자열를 개별 문자로 미리 분리
2. 문자열이 비어있을 때까지 반복
3. firstChar 변수를 통해 첫번 째 단어를 초기화
4. 리스트를 순회하면서 firstChar와 같은 문자가 나올 때마다 cnt1을 증가시키고,  
다른 문자가 나올 때마다 cnt2를 증가시킵니다.
5. cnt1과 cnt2가 같아지는 순간 반복을 멈춥니다. 
6. 분리된 부분 문자열 카운트 증가
7. 분리된 문자열 제거
8. 결과 반환