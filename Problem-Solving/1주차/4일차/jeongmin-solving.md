## 코드

```java
class Solution {
    public int solution(String s) {
        int answer = 0; // 분해한 문자열 카운트
        int cnt = 0; // 전테 글자 수  카운트

        while(s.length() > 0){
            char x = s.charAt(0); // 첫 글자 x.
            int xCnt = 1; // x의 카운트. 숫자를 1로 초기화 (자신을 포함하여 1로 시작)
            int otherCnt = 0; // x가 아닌 글자의 카운트.
            cnt = 0; // 전체 글자 수 카운트를 초기화함

            for(int i = 1; i < s.length(); i++){ // 1로시작하여 x의 다음 글자를 받는다
                if(x == s.charAt(i)) xCnt++; //x와 다음 글자가 같다면 xCnt를 카운트한다.
                else otherCnt++; //x와 다음 글자가 다르면 otherCnt를 카운트한다.
                if(xCnt == otherCnt) { //xCnt와 otherCnt가 같다면 조건을 만족했음
                    cnt = xCnt + otherCnt; // 문자열이 aaaab 나 a 인 상황일때 무한 while 처리를 위해 문자열 카운트한걸 더해줌.
                    s = s.substring(i + 1); // 조건을 만족한 문자열을 분해하고 남은 문자열 반환.
                    answer++; // 분해한 문자열를 1카운트함.
                    break; //조건을 만족했으므로 for종료
                }
            }
            if(cnt == 0) return answer + 1; // cnt를 확인하여 0이면 문자열이 aaab나 a같은 상황이므로 answer에 더해주고 값을 반환
        }
        return answer; // 최종 카운트값 반환
    }
}
```

## 해설

로직은 문자열이 1이상일때까지 반복문을 돌면서 x값과 다른값을 카운트하고 비교하여 같으면 분해한 카운트를 올려주고 남은 문자열을 다시 문자열에 넣어준다.
여기서 aaab, a같은 것들이 들어가면 문자열이 나눠지지 않으므로 전체 cnt를 추가하여 처리해 주었다.
