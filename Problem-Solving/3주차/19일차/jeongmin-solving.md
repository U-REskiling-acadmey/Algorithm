## 코드

```java
class Solution {
    public int solution(int a, int b, int n) {
        int answer = 0;

        while(n >= a){
            answer += (n/a)*b; // 받는 콜라의 누적값
            n = (n/a)*b + n%a; // 새로운 빈병 수
        }

        return answer;
    }
}
```

## 해설

빈 병으로 새 콜라를 바꿀 수 없을 때까지 얻은 콜라의 수를 구해야한다.<br>
while을 통해 빈 병의 수가 새 콜라로 교환해주는 병의 수보다 크거나 같게 조건을 정해주고<br>
answer에 콜라로 교환한 수를 누적해주고 이후 남은 생길 빈 병 수를 구하면서 while문이 끝나게 되면 답이 나온다.
