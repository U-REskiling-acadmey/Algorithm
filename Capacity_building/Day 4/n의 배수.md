## 나의 풀이
```java
class Solution {
    public int solution(int num, int n) {
        return num%n==0?1:0;
    }
}
```

아무래도 문제가 초간단 코드라고 할 수 있다. 조건이 num이 n의 배수이면 1을 아니면 0을 반환하는 문제인데  
나는 삼항 연산자를 사용해서 초간단으로 문제를 해결했다.

## 다른 사람의 풀이
```java
class Solution {
    public int solution(int num, int n) {
        int answer = 0;
        if(num % n == 0){
            answer = 1;
        } else {
            answer = 0;
        }
        return answer;
    }
}
```
나랑 비슷하게 푸신 분이 대부분이고 이렇게 정석으로 푸신 분이 몇분 계셨다. 거의 비슷하게 푸셔서 이번 건  
따로 설명을 달지는 않겠다.