## 문제 풀이
```java
class Solution {
    public int solution(int[] a, int[] b) {
        int result = 0;
        
        for(int i=0;i<a.length;i++){
            result += a[i]*b[i];
        }
        return result;
    }
}
```

a[0]*b[0] + a[1]*b[1] + ... + a[n-1]*b[n-1] 의 값을 구하는 문제인데 a의 b의 길이 값은 같으니  
반복문을 통해 결과값을 반환해주면 됩니다.