## 작성 코드
```java
class Solution_1{
    public String[] solution(String[] players, String[] callings){
        String[] answer = players;

        Map<String, Integer> map = new HashMap<>();

        for(int i=0; i<players.length; i++) map.put(players[i], i);

        for(int i=0; i<callings.length; i++) {
            // 이름 불린 선수의 원래 등수
            int rank = map.get(callings[i]);
            // 순위가 바뀔 선수의 이름
            String name = answer[rank-1];
            // 선수 등수 변경
            answer[rank-1] = answer[rank];
            answer[rank] = name;
            map.put(answer[rank-1], rank-1);
            map.put(answer[rank], rank);
        }

        return answer;
    }
}
```

map에 선수들의 이름과 순위를 넣어준 뒤 선수 이름이 호명될 때마다 순위를 가져와 변경해준다.