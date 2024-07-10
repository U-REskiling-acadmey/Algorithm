## 코드

```java
class Solution {
    public long solution(int a, int b) {
        // 작은수, 큰수 지정
        int min = Math.min(a, b);
        int max = Math.max(a, b);

        long answer = 0;

        for(int i=min; i<=max; i++) answer+=i;

        return answer;
    }
}
```

## 해설

a와 b사이의 모든 수의 합이므로 for문을 사용해 작은수부터 차례대로 더해준다<br/>
a,b는 대소관계가 정해저있지 않기 때문에 min, max를 지정한다.
