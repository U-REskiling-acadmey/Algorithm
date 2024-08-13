## 코드

```java
class Solution {
    public int solution(int left, int right) {
        int answer = 0;

        for(int i=left; i<=right; i++){
            int cnt = divisorCnt(i);
            if(cnt%2 == 0) answer+=i;
            else answer-=i;
        }

        return answer;
    }

    public int divisorCnt(int num) {
        int cnt = 0;
        for (int i=1; i*i <= num; i++) {
            if (num%i == 0) {
                cnt++;
                if (i != num/i) cnt++;
            }
        }
        return cnt;
    }
}
```

## 해설

주어진 2개의 수 사이 값들의 약수의 개수가 짝수, 홀수임을 판별하여 값을 구한다.<br>

1. for를 이용해 left~right 값을 이용한다.
2. divisorCnt 함수를 만들어 약수의 개수를 구한다.
3. divisorCnt를 이용해 구한 약수의 개수의 홀짝을 판별하여 answer에 더하거나 빼준다.
