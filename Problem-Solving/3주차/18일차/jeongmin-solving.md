## 코드

```java
class Solution {
    public int solution(int n) {
        for (int i = 2; i < n; i++) {
            if (n % i == 1) return i;
        }
        return 0;
    }
}
```

## 해설

n을 어떤수로 나눴을때 1이되는 가장 작은 어떤수를 구해야 된다 <br>
for을 이용해 작은 수 부터 차례대로 n을 나누면서 나머지가 1인 수를 구했습니다.
