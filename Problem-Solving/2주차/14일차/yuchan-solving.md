## 문제 풀이 과정
두 정수 a와 b가 주어졌을 떄 a와 b 사이에 속한 모든 정수의 합을 리턴하는 함수를 만들어야 한다.  
그렇다면 a와 b 사이 만큼 더해주어서 반복해야 한다고 생각해보자.

for문으로 구현할 수 있다. 코드는 다음과 같다.
```java
for(int i=a;i<=b;i++){

}
```

문제를 보면 long 타입으로 반환 타입이 지정되어 있다. 아마도 long 타입으로 반환하라는 문제인거 같다.  
코드를 작성해보면 다음과 같다.

```java
long answer = 0;
for(int i=a;i<=b;i++){
    answer += i;
}
```

그래서 테스트 코드를 실행해보니 a의 값과 b의 값이 정해지지 않다는 것을 알게 되었다.  
그래서 이를 큰값과 작은 값으로 변경해줄 위치 변환이 필요하다. 코드는 다음과 같다.

```java
if(a > b){
    int temp = a;
    a = b;
    b = temp;
}
```

완성된 코드는 다음과 같다.
```Java
class Solution {
    public long solution(int a, int b) {
        long answer = 0;
        
        if(a > b){
            int temp = a;
            a = b;
            b = temp;
        }
        
        for(int i=a;i<=b;i++){
            answer += i;
        }
        return answer;
    }
}
```

코드를 줄일 수 있는 방법을 없을까? 고민이 된다. 예전에 기억하기에는 이러한 for문을 줄일 수 있던걸로 알고 있다.  
두 숫자 사이의 합을 구하는 방식 중에 가우스의 덧셈 공식이라고 이 공식을 사용하게 되면 반복문은 불필요하다고 할 수 있다.  
코드는 다음과 같다.

```Java
(long) (b - a + 1) * (a + b) / 2;
```

음.... 생각해보니 Math를 사용해서 구분해줄 수 있지 않을까? 생각이 들었다. 왜냐하면 Math에는 작은 값과 큰 값을 구별해주는  
기능이 있기 때문에 그 구별을 통해 min과 max를 가우스 덧셈 공식에 넣으면 될 것 같다는 생각이 들었다.
```java
int min = Math.min(a, b);
int max = Math.max(a, b);
return (long) (max - min + 1) * (min + max) / 2;
```

## 최종 제출 코드
```java
class Solution {
    public long solution(int a, int b) {
        int min = Math.min(a, b);
        int max = Math.max(a, b);
        return (long) (max - min + 1) * (min + max) / 2;
    }
}

```
