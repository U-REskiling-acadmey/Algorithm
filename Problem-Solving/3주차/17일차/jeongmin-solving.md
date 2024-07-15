## 코드

```java
class Solution {
    public int solution(int[] nums) {
        int answer = 0;
        boolean isprime = false;

        for(int i=0; i<nums.length; i++){
            for(int j=i+1; j<nums.length; j++){
                for(int z=j+1; z<nums.length; z++){
                    isprime = false;
                    int sum = nums[i] + nums[j] + nums[z];
                    isprime = isPrime(sum);
                    if(isprime) answer+=1;
                }
            }
        }
        return answer;
    }

    public boolean isPrime(int n) {
        if (n <= 1) return false;
        for (int i = 2; i < n; i++) {
            if (n % i == 0) return false;
        }
        return true;
    }
}
```

## 해설

3개를 더했을 때 소수가 되는 경우의 수를 구해야한다. <br/>
반복문을 통해서 경우를 수를 구하면서 isPrime함수를 만들어 소수를 판별해주었습니다.<br/>
