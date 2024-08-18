## 문제풀이 27일차 : 과일 정수
이번 문제는 정말 많은 고난과 시간을 할애했다고 할 수 있다. 일단 가장 먼저 이전 26이차 문제에서 정렬을 `Array.sort()` 를  
사용하지 않고 구현을 하겠다고 말을 했기 때문에 정렬을 순수 알고리즘으로 구현하고 싶었다.

그래서 가장 흔히 사용되는 선택 정렬을 통해서 구현을 먼저 해보았다.

```java
private static void selection_sort(int[] num,int size){
    for(int i=0;i<size-1;i++){
        int min_index = i;

        // 최솟값을 가지는 인덱스 찾기
        for(int j = i+1; j<size;j++){
            if(num[j] < num[min_index])min_index = j;
        }

        // i번째 값과 찾은 최솟값을 서로 교환
        swap(num, min_index, i);
    }
}

private static void swap(int[] num,int i, int j){
    int temp = num[i];
    num[i] = num[j];
    num[j] = temp;
}
```

하지만 역시는 역시 알고리즘 문제를 풀면서 가장 만나기 싫은 런타임에러가 발생했다. 처음에는 왜 이게 런타임 에러가 뜨지? 정말 많이 고민했다.  
문제의 제한 사항을 잘 살펴봤어야 했다....알고 보니 선택 정렬은 큰 배열을 정렬하는 것은 비효율적이며 시간이 초과될 수 있다고 한다.  
(정렬 공부 다시 해야겠다...이런 기초적인 것도 생각 안하고 막 구현하다니)

그래서 문제 제한 사항을 다시 살펴보았다.

### 제한사항
- 3 ≤ k ≤ 9
- 3 ≤ m ≤ 10
- 7 ≤ score의 길이 ≤ 1,000,000
- 1 ≤ score[i] ≤ k
이익이 발생하지 않는 경우에는 0을 return 해주세요.

이런 제한 사항을 가지고 있었다. 그럼 이렇게 큰 score의 길이를 어떻게 해야 정렬할 수 있을까? 예전에 알고리즘 문제 풀이 책에서 재귀적으로 배열을  
분할해서 분할된 배열을 병합하여 정렬하는 코드가 기억이 났다.

그래서 다음과 같이 구현을 했다.

```java
// 병합 정렬 메서드
    private static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            // 배열을 중간에서 나누기
            int mid = (left + right) / 2;

            // 좌측 절반 정렬
            mergeSort(arr, left, mid);

            // 우측 절반 정렬
            mergeSort(arr, mid + 1, right);

            // 두 정렬된 부분 배열을 병합
            merge(arr, left, mid, right);
        }
    }

    // 두 개의 정렬된 하위 배열을 병합하는 메서드
    private static void merge(int[] arr, int left, int mid, int right) {
        // 두 부분 배열의 크기
        int n1 = mid - left + 1;
        int n2 = right - mid;

        // 임시 배열 생성
        int[] L = new int[n1];
        int[] R = new int[n2];

        // 부분 배열 복사
        for (int i = 0; i < n1; i++) {
            L[i] = arr[left + i];
        }
        for (int j = 0; j < n2; j++) {
            R[j] = arr[mid + 1 + j];
        }

        // 병합 과정
        int i = 0; // L 배열의 인덱스
        int j = 0; // R 배열의 인덱스
        int k = left; // 원래 배열의 인덱스

        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k++] = L[i++];
            } else {
                arr[k++] = R[j++];
            }
        }

        // 남은 요소 복사
        while (i < n1) {
            arr[k++] = L[i++];
        }
        while (j < n2) {
            arr[k++] = R[j++];
        }
    }
}
```

진짜 이 코드 구현하는데 내리 2시간은 사용한거 같다.....솔직히 코딩테스트 푸는데 이런 시간 걸리면 좀 그러지 않나 생각하는데  
난 보는 시선이 다르다. 일단 난 순수하게 함수를 사용하지 않고 알고리즘을 구현하는 것이 목표이다. 즉, 내 코딩 실력을 키우는게 목표이기 때문에 좋은 방법이라고 생각한다.

이제 최종적으로 문제를 구현해보자 우선 문제의 목표는 과의 점수에 따라 상자당 가격이 결정되며, 가능한 최대 이익을 얻기 위해서는 높은 점수의 사과를 최대한 많이 상자에 담는 것이 중요하다.  
최대 이익을 계산해야 하기 때문에 배열을 끝에서부터 m개씩 묶어가면서, 상자당 최소 점수를 곱하여 이익을 계산한다. 정렬된 배열에서 마지막부터 m개씩 묶는 것이므로, 높은 점수의 사과를 최대한 많이 사용하게 된다.

이렇게 check() 함수를 구현하면 다음과 같이 구현할 수 있다.

```java
private static int check(int[] num, int k, int m) {
    int ret = 0;

    // 점수가 높은 사과들을 최대한 m개씩 상자에 담아야 하므로,
    // 배열을 뒤에서부터 m개씩 묶어서 계산합니다.
    for (int i = num.length - m; i >= 0; i -= m) {
        ret += num[i] * m;
    }

    return ret;
}
```

## 전체 코드
```java
class Solution {
    public int solution(int k, int m, int[] score) {
        // 1. 사과 점수를 병합 정렬로 오름차순으로 정렬
        mergeSort(score, 0, score.length - 1);

        // 2. 최대 이익 계산
        return check(score, k, m);
    }

    // 병합 정렬 메서드
    private static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            // 좌측 절반 정렬
            mergeSort(arr, left, mid);
            // 우측 절반 정렬
            mergeSort(arr, mid + 1, right);

            // 두 부분을 병합
            merge(arr, left, mid, right);
        }
    }

    // 배열 병합 메서드
    private static void merge(int[] arr, int left, int mid, int right) {
        // 부분 배열의 크기
        int n1 = mid - left + 1;
        int n2 = right - mid;

        // 임시 배열 생성
        int[] L = new int[n1];
        int[] R = new int[n2];

        // 부분 배열 복사
        System.arraycopy(arr, left, L, 0, n1);
        System.arraycopy(arr, mid + 1, R, 0, n2);

        // 병합 과정
        int i = 0, j = 0;
        int k = left;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k++] = L[i++];
            } else {
                arr[k++] = R[j++];
            }
        }

        // 남은 요소 복사
        while (i < n1) {
            arr[k++] = L[i++];
        }
        while (j < n2) {
            arr[k++] = R[j++];
        }
    }

    private static int check(int[] num, int k, int m) {
        int ret = 0;

        // 점수가 높은 사과들을 최대한 m개씩 상자에 담아야 하므로,
        // 배열을 뒤에서부터 m개씩 묶어서 계산합니다.
        for (int i = num.length - m; i >= 0; i -= m) {
            ret += num[i] * m;
        }

        return ret;
    }
}
```