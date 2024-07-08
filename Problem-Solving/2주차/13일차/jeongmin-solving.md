## 코드

```java
class Solution {
    public int solution(int[] numbers) {
        int answer = 45;

        for(int num: numbers) answer -= num;

        return answer;
    }
}
```

## 해설

0부터 9까지 모두 다른 숫자 중 없는 숫자의 합을 반환하면 되므로 0부터9까지의 합 45에서 주어진 배열의 수들을 빼서 답을 구했습니다.
