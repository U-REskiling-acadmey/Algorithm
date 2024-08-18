## 문제 풀이 : 둘만의 암호
```java
class Solution {
    public String solution(String s, String skip, int index) {
        String answer = "";

        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            for (int j = 0; j < index; j++) {
                c += 1;
                if (c > 'z') {
                    c -= 26;
                }
                if (skip.contains(String.valueOf(c))) {
                    j--;
                }
            }
            answer += c;
        }

        return answer;
    }
}
```

이 문제는 주어진 문자열 `s`의 각 문자를 주어진 `index` 만큼 알파벳 순서에서 이동시키되 `skip` 문자열에 포함된  
알파벳은 건너뛰고, 알파벳이 `z` 를 넘어가는 경우 다시 `a` 로 돌아가도록 변환하는 문제입니다.

그래서 2중 for를 통해서 구현했습니다. 첫번째 for문은 s 문자열을 순회하고 각 문자를 c에 가져와서 변환하는 작업을 통해서  
c를 idex 만큼 이동시키는데, 이 때 z를 넘어가는 경우를 처리합니다.

그리고 마지막에 contains를 통해서 skip에 포함된 문자는 무시하도록 조건을 추가해주면 구현할 수 있습니다.g