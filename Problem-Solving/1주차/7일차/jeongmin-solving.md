## 코드

```java
class Solution {
    public String solution(int[] food) {
        String answer = "0";
        StringBuffer sb = new StringBuffer();

        for(int i=1; i<food.length; i++){
            int foodN = food[i]/2;
            if(foodN >= 1){
                for (int j=0; j<foodN; j++) sb.append(i);
            }
        }

        answer = sb + answer;
        answer += sb.reverse();

        return answer;
    }
}
```

## 해설

음식 수를 2로 나눴을때 1이상인 것들만 순서대로 넣고 0과 reverse시킨 값을 넣었습니다.
