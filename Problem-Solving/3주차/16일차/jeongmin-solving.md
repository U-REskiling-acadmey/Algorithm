## 코드

```java
class Solution {
    public String solution(String phone_number) {
        String[] answer = phone_number.split("");
        for(int i=0; i<answer.length-4; i++) {
            answer[i] = "*";
        }
        return String.join("", answer);
    }
}
```

## 해설

뒷 4자리를 제외하고 전부 \*로 바꿔야되기 때문에, 우선 문자열을 배열로 나눈후 <br/>
for를 이용해 전체 길이의 -4만클 \*로 바꾸고 join을 이용해 문자열로 반환하였습니다.
