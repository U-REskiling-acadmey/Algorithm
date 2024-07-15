## 문제 풀이
```java
class Solution {
    public int solution(int[] nums) {
        int answer = 0;

        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                for (int z = j + 1; z < nums.length; z++) {
                    int sum = nums[i] + nums[j] + nums[z];
                    if (isPrime(sum)) {
                        answer++;
                    }
                }
            }
        }

        return answer;
    }

    public boolean isPrime(int n) {
        if (n <= 1) return false;
        if (n == 2) return true;
        if (n % 2 == 0) return false;

        for (int i = 3; i <= Math.sqrt(n); i += 2) {
            if (n % i == 0) return false;
        }
        return true;
    }
}
```

## 문제 접근 방식
문제는 배열에서 3개의 수를 골라 그 합이 소수가 되는 경우의 수를 구하는 것입니다.  
이를 위해 3중 반복문을 통해 배열의 모든 조합을 검사하고, 각 조합의 합이 소수인지 확인합니다.