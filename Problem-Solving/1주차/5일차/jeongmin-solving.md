## 코드

```java
class Solution {
    public int solution(String t, String p) {
        int answer = 0;
        int len = p.length();

        for(int i=0; i<=t.length()-len; i++){ // 전체길이에 p의 길이를 빼주어 for가 오버되지않게 한다.
            String st = t.substring(i, i+len); // p의 길이만큼 문자열을 자흔다.
            if(Long.parseLong(st) <= Long.parseLong(p)){ // p와 비교후 카운트
                answer ++;
            }
        }

        return answer;
    }
}
```

## 해설

for를 이용해 문자열 첫번째부터 p와 같은 길이만큼 잘라내고 문자열을 long으로 바꾼 후 비교하여 답을 카운트함

- p의 길이가 18까지 이므로 Integer.parseInt는 에러가 발생한다.
