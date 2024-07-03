## 문제 풀이

```java
import java.util.*;
class Solution {
    public int solution(int n, int[] lost, int[] reserve) {
        int[] students = new int[n];
        Arrays.fill(students, 1);

        for (int l : lost) students[l - 1]--;
        for (int r : reserve) students[r - 1]++;

        for (int i = 0; i < n; i++) {
            if (students[i] == 0) {
                if (i > 0 && students[i - 1] == 2) {
                    students[i]++;
                    students[i - 1]--;
                } else if (i < n - 1 && students[i + 1] == 2) {
                    students[i]++;
                    students[i + 1]--;
                }
            }
        }

        int count = 0;
        for (int student : students) {
            if (student > 0) {
                count++;
            }
        }

        return count;
    }
}
```

학생 수에 맞게 students 변수에 Array.fill 를 통해 상태를 1로 전부 초기화 해줍니다.  이후 lost 배열을 돌면서 체육복을 도난당한 항상의 상태를 0으로 변경합니다.

reserve 배열을 돌면서 여벌 체육복을 가진 학생의 상태를 2로 변경합니다. 이후 students 배열을 돌면서 체육복이 없는 학생(상태가 0)을 찾습니다.

그 학생의 앞번호, 뒷번호 학생이 여벌 체육복이 있는지 확인하고, 있다면 체육복을 빌려줍니다.