## 완성 코드
```java
class Solution{
    public int solution(String s) {
        // String과 같은 객체 타입은 강제 타입 변환으로 변경이 불가능하다.
        // 그렇기 때문에 이와 같이 Integer.parseInt()와 같은 메소드로 변경해야 합니다.
        int answer = Integer.parseInt(s);
        return answer;
    }
}
```

여기서 주의해야 될 점은 타입 변환이다. 자바에서 사용되는 강제 타입 변환은 기본 타입(primitive type)에서만 가능하기  
때문에 타입 변환이 불가능하다. 그렇기 때문에 여기서는 `Integer.paresInt()`와 같은 메소드를 사용해야 한다.

문자열을 변혀잇키고 싶다면 이건 수학의 공식 같은 것이기 때문에 꼭 외우자!!