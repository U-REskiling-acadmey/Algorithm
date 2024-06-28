## 문제 풀이
```java
=class Solution {
    public String solution(int[] food) {
        String answer = "0";

        for (int i = food.length - 1; i > 0; i--) {
            for (int j = 0; j < food[i] / 2; j++) {
                answer = i + answer + i; 
            }
        }

        return answer;
    }
}
```

문제의 조건은 food의 0인덱스 값은 물이라 무조건 1로 들어오고 나머지 값들에 대해서 구해야 하는데  
나머지 값들의 값이 더이상 2로 나눠지지 않을 때까지 반복한 다음 역순으로 삽입하면 되는 문제이다.