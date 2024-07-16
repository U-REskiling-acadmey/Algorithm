## 문제 풀이 

```java
class Solution {
    public int solution(int n) {
        int answer = 0;
    
        for(int i=1;i<=n;i++){
            answer = n % i ==1 ? answer==0? i : answer > i ? i:answer : answer;
        }
        
        return answer;
    }
}
```

이번 문제는 삼항 연산자를 통해서 조건을 구분해주었다. n에서 i 값을 나누었을 때 몫 값이 가장 작은 값을 구해야 하기 때문에  
여러 조건문을 적용해주어야 한다. 그렇기 때문에 다음과 같은 코드로 작성했다.