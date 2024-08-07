## 문제 풀이
```java
class Solution {
    public String solution(String number, int k) {
        int idx=0;

        StringBuilder str = new StringBuilder();
        for(int i=0;i<number.length()-k;i++){
            char max = 0;
            for(int j=idx;j<=i+k;j++){
                if(max < number.charAt(j)){
                    max = number.charAt(j);
                    idx = j+1;
                }
            }
            str.append(max);
        }
        
        return str.toString();
    }
}
```

문제는 k개의 수를 제거했을 때 얻을 수 있는 가장 큰 숫자를 구하는 문제였다.  
이때 나는 2중 for를 통해서 하나 하나 구분해서 분리해주는 코드를 작성해보았다.

예를 들어 number의 값이 1924고 k의 값이 2라고 해보자 처음 for문은 number의 길이 만큼 - k 이기 때문에 2번 반복한다.  
그 다음 for문은 큰 수 값을 얻었을 때 str에 넣어준다. 이러면 str에 값에는 9와 4의 값이 들어간다 4개의 숫자중 2개 중에서 가장 큰 수이기 때문