## 코드

```java
class Solution {
    public int solution(String name) {
        int answer = 0;
        char[] al = name.toCharArray();
        int len = al.length; //길이
        int move = al.length-1; //한 방향으로 이동했을때 움직인 수 (좌우)

        for (int i=0; i<len; i++){
            answer += Math.min(al[i] - 'A', 'Z' - al[i]+1); //알파벳 이동 최소길이(A에서 다음, 이전)(Z는+1해야 A에서 출발한 수가 맞음)(위,아래)

            // 연속된 A가 끝나는 인덱스 값 구하기
            int next = i+1;
            while(next<len && al[next] == 'A'){
                next++;
            }

            // 좌우이동 비교 (둘이 이동 경로는 A기준 반대)
            move = Math.min(move, (i*2) + len - next); // i만큼 다음으로 이동하고 A를 만났을때 이전으로 가는 경우 비교
            move = Math.min(move, (len-next)*2 + i); // 처음부터 이전으로 이동하고 A를 만났을때 다음으로 가는 경우 비교
        }
        answer += move;

        return answer;
    }
}
```
