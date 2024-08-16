## 문제풀이 : 두 개 뽑아서 더하기
```java
import java.util.*;

class Solution {
    public int[] solution(int[] numbers) {
        Arrays.sort(numbers);  // 배열 정렬

        // 초기 빈 배열을 null로 설정
        int[] answers = null;

        // 모든 조합의 합 계산
        for (int i = 0; i < numbers.length; i++) {
            for (int j = i + 1; j < numbers.length; j++) {
                answers = check(numbers[i], numbers[j], answers);
            }
        }
        
        Arrays.sort(answers); // 최종 배열을 정렬
        return answers;
    }
    
    public int[] check(int a, int b, int[] answers) {
        int sum = a + b;

        if (answers == null) {
            // 처음 호출될 때 새 배열 생성
            answers = new int[1];
            answers[0] = sum;
        } else {
            // 중복 여부 체크
            boolean exists = false;
            for (int i = 0; i < answers.length; i++) {
                if (answers[i] == sum) {
                    exists = true;
                    break;
                }
            }
            // 중복이 아니라면 배열에 추가
            if (!exists) {
                int[] new_answer = new int[answers.length + 1];
                for (int i = 0; i < answers.length; i++) {
                    new_answer[i] = answers[i];
                }
                new_answer[answers.length] = sum;
                answers = new_answer;
            }
        }

        return answers;
    }
}
```

26일차 이후로는 앞으로 이렇게 함수를 사용하지 않고 순수 알고리즘으로 문제를 해결해보려고 한다. 아 생각해보니...정렬을 구현을 안 했네...  
다음 문제에서 정렬 문제가 나오면 정렬도 직접 구현하자...문제 해설은 다음과 같다.

우선 문제를 확인해보면서 처음에 확인한것은 2중 반복문을 통해 더해줘야 하는 경우의 수를 모두 출력할 수 있냐의 초점을 맞췄다.  
`numbers.length`
```java
        int[] numbers = {2, 1, 3, 4, 1};
        Arrays.sort(numbers);

        for(int i=0;i<numbers.length;i++){
            for(int j=i+1;j<numbers.length;j++){
                System.out.println(numbers[i] +" "+numbers[j]);
            }
        }

결과
1 1
1 2
1 3
1 4
1 2
1 3
1 4
2 3
2 4
3 4
```

그럼 이렇게 경우의 수가 나왔을 때 이를 구분해주면서 `ArrayList`나 `Set`을 사용하지 않을 방법이 없을까? 고민을 많이 했다 그래서  
이를 체크해주는 함수를 따로 생성해주었다.

이 체크 함수에는 경우의 수의 값, 늘려나갈 `answers` 값이 필요하다 하지만 `List`를 사용하지 않고 배열을 다시 할당하면서 늘리려면 `answers`을 `null`로 선언해야 한다.  
이 부분은 꼭 체크하자
```java
// 초기 빈 배열을 null로 설정
int[] answers = null;

// 두 개 뽑아서 더하기를 위한 체크 함수 생성
public int[] check(int a, int b, int[] answers) {

}
```

이제 기능을 구현해보자 처음에는 그냥 값만 추가하면 된다. 만약 `answers`의 값이 null이면 반복문이나 다른 함수의 사용이 필요 없이  
그냥 값만 데입해주면 된다. 그 부분을 구현해보자

```java
if (answers == null) {
    // 처음 호출될 때 새 배열 생성
    answers = new int[1];
    answers[0] = sum;
}
```

이제 null이 아니면 `answers`의 길이 값을 늘려가면서 중복을 제거해서 값을 반환하는 else문을 만들면 된다.
```java
else {
    // 중복 여부 체크
    boolean exists = false;
    for (int i = 0; i < answers.length; i++) {
        if (answers[i] == sum) {
            exists = true;
            break;
        }
    }
    // 중복이 아니라면 배열에 추가
    if (!exists) {
        int[] new_answer = new int[answers.length + 1];
        for (int i = 0; i < answers.length; i++) {
            new_answer[i] = answers[i];
        }
        new_answer[answers.length] = sum;
        answers = new_answer;
    }
}
```

체크 함수를 전체적으로 합치면 다음과 같이 구현할 수 있다.

```java
public int[] check(int a, int b, int[] answers) {
    int sum = a + b;

    if (answers == null) {
        // 처음 호출될 때 새 배열 생성
        answers = new int[1];
        answers[0] = sum;
    } else {
        // 중복 여부 체크
        boolean exists = false;
        for (int i = 0; i < answers.length; i++) {
            if (answers[i] == sum) {
                exists = true;
                break;
            }
        }
        // 중복이 아니라면 배열에 추가
        if (!exists) {
            int[] new_answer = new int[answers.length + 1];
            for (int i = 0; i < answers.length; i++) {
                new_answer[i] = answers[i];
            }
            new_answer[answers.length] = sum;
            answers = new_answer;
        }
    }

    return answers;
}
```