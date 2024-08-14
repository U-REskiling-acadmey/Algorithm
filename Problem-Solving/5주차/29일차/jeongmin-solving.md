## 코드

```java
class Solution {
    public String solution(String s, String skip, int index) {
        String answer = "";
        char[] al = s.toCharArray();

        for(int i=0; i<al.length; i++) {
        	for(int j=0; j<index; j++) {
        		al[i]++;
                if(al[i] > 'z') {
        			al[i] -= 26;
    			}
                while(skip.contains(String.valueOf(al[i]))) {
        			al[i]++;
                    if(al[i] > 'z') {
        			    al[i] -= 26;
    			    }
        		}
        	}
        }

        answer = String.valueOf(al);
        return answer;
    }
}
```

## 해설

s의 각 앒파벳을 index만큼 뒤의 알파벳으로 바꾸는데 skip에 있는 알파벳은 제외하고 z를 넘으면 다시 a부터 시작한다.<br/>

1. char배열를 만들어 s값을 넣어준다.
2. al 길이만큼 for를 순회하면서 index만큼 알파벳을 뒤로 미룬다.
3. index만큼 미룰때 z를 넘어가면 -26으로 a로 돌아간다.
4. 그 후 미룬값이 skip에 포함되있는지 while로 포함된만큼 미룬다.(여기서도 z를 넘으면 a로 돌아간다)
5. 마지막으로 char배열을 string으로 바꿔준 후 return한다.
