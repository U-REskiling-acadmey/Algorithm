## 문제 풀이
```java
class Solution {
    public int solution(String t, String p) {
        int length = t.length() - p.length();
        long pNum = Long.parseLong(p);
        int answer = 0;

        for (int i = 0; i <= length; i++) {
            String temp = t.substring(i, i + p.length());

            if (Long.parseLong(temp) <= pNum) {
                answer++;
            }
        }
        return answer;
    }
}
```
반복문을 통해 문자열 t를 문자열 p의 길이만큼 잘라 p보다 작은 부분문자열 t의 개수를 구하는 문제입니다.
이때 조건이 t에서 p의 길이만큼의 부분 문자열을 추출할 수 있는 최대 시작 인덱스를 length에 저장하여 반복문을 돌립니다.
이후 문자열 temp의 값이 p보다 작은 경우 answer를 증가시킨다.