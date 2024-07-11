## 코드

```java
class Solution {
    static int cnt = 0;
    public int solution(int[] number) {
        dfs(0, 0, new boolean[number.length], number);
        return cnt;
    }

    static void dfs(int depth, int idx, boolean[] visited, int[] number) {
        // 깊이가 3이면 합을 구하여 0일 때 cnt에 1을 추가
        if (depth == 3) {
            int sum = 0;
            for (int i = 0; i < visited.length; i++) {
                if (!visited[i]) continue;
                sum += number[i];
            }
            if(sum == 0) cnt += 1;
            return;
        }

        for (int i = idx; i < number.length; i++) {
            if (visited[i]) continue;
            visited[i] = true;
            dfs(depth + 1, i + 1, visited, number);
            visited[i] = false;
        }
    }
}
```

## 해설

3명의 번호의 합이 0일 때 삼총사가 되기때문에 주어진 배열의 3개를 고르는 조합에서 그 합이 0인 것을 고르면 된다. <br/>
dfs알고리즘을 이용해 깊이가 3일때 합을 구하여 0이면 cnt를 추가하여 구했습니다.
