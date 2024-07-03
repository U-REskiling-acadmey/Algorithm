## 문제 풀이

문제의 조건은 다음과 같다. 

1. 최대한 다양한 종류의 폰켓몬을 가지길 원하기 때문에, 최대한 많은 종류의 폰켓몬을 포함해서 N/2마리를 선택하려 합니다.

중복을 제외하고 가장 많은 횟수를 구하는 문제이다. 그렇기 때문에 Set을 통해 중복을 제거하고 이후 사이즈를 구하는 문제를   
구현하면 된다.

```java
int max = nums.length / 2;
```

이후 Hashset을 통해 중복 제거를 해주면 
```java
HashSet<Integer> hashSet = new HashSet<>();

for(int i=0;i<nums.length;i++){
    hashSet.add(nums[i]);
}
```

예시 값이 [3,3,3,2,2,2] 일때 [2,3]으로 간추려 진다. 이때 여기서 조건을 max >= 보다 크면 hashSet을  
아니면 max 값을 반환 해주면 된다.


## 최종 코드
```java
import java.util.*;

class Solution {
    public int solution(int[] nums) {

        int max = nums.length/2;
        HashSet<Integer> hashSet = new HashSet<>();

        for(int i=0;i<nums.length;i++){
            hashSet.add(nums[i]);
        }

        if (max >= hashSet.size()) {
            return hashSet.size();
        } else {
            return max;
        }
    }
}
```