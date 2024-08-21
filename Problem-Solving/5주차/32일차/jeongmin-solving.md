## 코드

```java
class Solution {
    public int solution(int n) {
        String answer = "";

        while (n != 0) {
            answer += n%3;
            n /= 3;
        }

        return Integer.parseInt(answer, 3);
    }
}
```

1. answer += n%3를 하여 3진법으로 바꿔준다 (이러면 이미 뒤집어져있다)
2. Integer.parseInt로 다시 10진법으로 바꾸어준다.
