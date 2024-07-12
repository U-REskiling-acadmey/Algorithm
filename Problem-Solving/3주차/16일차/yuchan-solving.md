## 풀이 과정

이번 문제는 전화번호 뒷 4자리를 남기고 나머지 숫자를 모두 `*` 로 만드는 문제이다.  
그럼 나는 변경이 쉬운 StringBuilder를 사용해서 charAt을 통해 `*` 변경해보려고 한다.

코드는 다음과 같다.
```java
StringBuilder sb = new StringBuilder(phone_number);
for (int i = 0; i < phone_number.length() - 4; i++) {
    sb.setCharAt(i, '*');
}
return sb.toString();
```

이렇게 하면 변경이 자유로운 StringBuilder에 sb를 처음부터 -4 즉, 뒤 4자리르 제외한  
나머지를 `*`로 변경할 수 있다.

## 최종 코드
```java
import java.util.*;

class Solution {
    public String solution(String phone_number) {
        StringBuilder sb = new StringBuilder(phone_number);
        for (int i = 0; i < phone_number.length() - 4; i++) {
            sb.setCharAt(i, '*');
        }
        return sb.toString();
    }
}
```