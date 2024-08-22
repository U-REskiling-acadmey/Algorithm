## 코드

```java
class Solution {
    public int[] solution(String s) {
        int[] answer = new int[s.length()];

         for(int i=0; i<s.length(); i++){
            int idx = s.substring(0,i).lastIndexOf(s.charAt(i));
            if(idx != -1){
                answer[i] = i-idx;
            }
            else answer[i] = -1;
        }
        return answer;
    }
}
```

1. substring(0,i)로 비교할 크기만큼 잘라준다(s.chatAt(i)의 앞까지 자른다)
2. 그리고 lastIndexOf(s.chatAt(i))로 가까운 같은 글자의 인덱스를 구한다
3. 만약에 인덱스를 찾았다면 answer[i]에 idx 값을 넣어주고 아니면 -1를 넣는다.
