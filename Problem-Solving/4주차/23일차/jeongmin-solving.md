## 코드

```java
import java.util.Stack;
class Solution {
    public String solution(String number, int k) {
        char[] answer = new char[number.length() - k];
        Stack<Character> stack = new Stack<>();

        for(char num: number.toCharArray()){
            while (!stack.empty() && stack.peek() < num && k>0){
                stack.pop();
                k--;
            }
            stack.push(num);
        }

        for(int i=0; i<answer.length; i++){
            answer[i] = stack.get(i);
        }

        return new String(answer);
    }
}
```

## 해설

k개의 숫자를 제외했을 때 가장 큰 숫자를 구해야 한다. <br>
num을 스택에 넣으면서 while로 이전 스택값이 num보다 작으면 pop을 해주고k>0일때까지 k-1를 반복해준다. <br>
이렇게 하면 k만큼 제거하면서도 가장 큰값을 얻을 수 있다.
