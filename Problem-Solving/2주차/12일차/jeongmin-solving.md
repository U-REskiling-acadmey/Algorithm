## 코드

```java
class Solution {
    public int solution(String s) {
        int answer = 0;
        String[] nums = new String[]{"zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine"};

        for(int i=0; i<10; i++){
            s = s.replaceAll(nums[i], i+"");
        }

        return Integer.parseInt(s);
    }
}
```

## 해설

replaceAll 함수를 사용해 nums 배열에 각각 해당하는 값을 치환해 풀었습니다.
