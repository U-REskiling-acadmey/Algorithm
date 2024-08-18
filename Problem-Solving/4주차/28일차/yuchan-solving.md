## 문제 풀이 28일차 : 약수의 개수와 덧샘
```java
class Solution {
    public int solution(int left, int right) {
        int cnt = 0;
        int sum = 0;

        for(int i=left;i<=right;i++){
            for(int j=1;j<=i;j++){
                if(i%j==0) {
                    cnt+=1;
                }
            }
            if(cnt%2==0) sum+=i;
            else sum-=i;
            cnt = 0;
        }
        
        return sum;
    }
}
```

이번 문제는 함수를 사용할 필요가 없었다. cnt 부분을 충분히 따로 함수로 분리해주어도 되지만 이번에는 간단하게 2중 for문으로  
구현해주었다.