## 문제 풀이
```java
class Solution {
    public int solution(int a, int b, int n) {
        int result = 0;

        while(n >= a){
            result += b * (n/a);
            n = (n/a) * b + (n%a);
        }

        return result;
    }
}
```

이 문제는 a개당 b개를 주는 문제이기 때문에 나누기 a를 하면 된다.  
그리고 b개를 얻는 문제이기 때문에 a개로 나눈 몫에 b개를 곱해서 더해주면 된다.