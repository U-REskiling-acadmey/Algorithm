## 코드

```java
class Solution {
    public long solution(int price, int money, int count) {
        long sum = 0;
        for(int i=1; i<=count; i++){
            sum += price*i;
        }
        return Math.max(0, sum - money);
    }
}
```

놀이기구를 타는데 부족한 금액을 반환한다.

1. for를 이용해 놀이기구 총 필요 금액을 구한다.
2. Math.max로 0과 sum-money를 비교하여 큰 수를 구한다.(sum-money는 부족한 금액)
