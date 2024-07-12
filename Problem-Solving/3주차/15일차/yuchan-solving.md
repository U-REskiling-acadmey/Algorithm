## 문제 풀이 과정

경우의 수를 탐방하는 문제인것 같다 이번 문제는 그렇기 때문에 이걸 반복문을 통해서 구분하려고 한다.  
`number` 배열이 `-2, 3, 0, 2, -5` 이라고 가정해보자 그럼 첫 인덱스가 -2 일때 다음 수를 구분하려면  
반복문에서 +1을 해주면 된다. 그러면 i가 -2일때 j는 3,0,2,-5를 반복할 수 있다. 이때 한가지 수를 더 얻어야 한다  

문제는 삼총사라는 문제이기 때문에 삼중 반복문을 이러한 반복문 형식으로 작성하면 다음과 같은 코드가 작성된다.

```java
for(int i = 0; i < number.length; i++) {
    for(int j = i + 1; j < number.length; j++) {
        for(int k = j + 1; k < number.length; k++) {
        }
    }
}
```

이제 여기서 조건을 작성해주어야 한다. number[i], number[j], number[k] 값을 더했을 때 0이 나와야 한다.  

```java
if(number[i] + number[j] + number[k] == 0) {
    answer++;
}
```

## 최종 코드
```java
class Solution {
    public int solution(int[] number) {
        int answer = 0;

        for(int i = 0; i < number.length; i++) {
            for(int j = i + 1; j < number.length; j++) {
                for(int k = j + 1; k < number.length; k++) {
                    if(number[i] + number[j] + number[k] == 0) {
                        answer++;
                    }
                }
            }
        }
        
        return answer;
    }
}
```