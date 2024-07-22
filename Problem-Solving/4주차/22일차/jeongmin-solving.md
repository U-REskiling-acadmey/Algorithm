## 코드

```java
class Solution {
    public int solution(int[] absolutes, boolean[] signs) {
        int answer = 0;

        for(int i=0; i<absolutes.length; i++){
            answer += signs[i] ? absolutes[i] : -absolutes[i];
        }

        return answer;
    }
}
```

## 해설

삼항연산자를 사용해서 signs가 ture면 absolutes의 부호를 정해서 answer에 더해주었습니다.
