---
title: "Quicksort"
last_modified_at: 2023-12-13
categories:
  - Algorithm
tags:
  - Solting
toc: true
toc_sticky: true
toc_label: "Quicksort"
---

# 퀵 정렬 알고리즘

## 퀵 정렬이란?

![image](https://github.com/xkimido/xkimido.github.io/assets/96900790/81db4093-c773-4abe-88bd-2b30de09a7f2){: .align-center}

- 퀵 정렬은 **분할 정복 알고리즘**이다.
-  이름 그대로 다른 정렬 알고리즘에 비해 빠른 속도가 장점이다.
- 불안정한 정렬이라는 특징이 있어서 값이 동일한 항목들의 순서를 보장하지 않는다.
- 배열에서 피벗`pivot` 요소를 선택하고 다른 요소들이 피벗보다 큰지 작은지에 따라 두 개의 하위 배열로 나눈다. 피벗을 어떤 기준으로 선택하느냐에 따라 성능이 달라진다.

### 퀵 정렬 알고리즘의 흐름

>
**분할 Divide**: 하나의 요소를 피벗으로 선택하고, 이를 기준으로 작은 요소들은 피벗의 왼쪽, 큰 요소들은 피벗의 오른쪽으로 이동시킨다.<br>
**정복 Conquer**: 피벗을 기준으로 배열을 두 부분으로 나누고, 각 부분을 재귀적으로 반복한다.<br>
**결합 Combine**: 부분 배열들이 정렬되면, 결합하여 전체 배열을 완성한다.

## Java 예제

```java
public void quickSort(int[] arr, int left, int right) {
    // base condition
    if (left >= right) {
        return;
    }
    int pivot = arr[right];
    
    int sortedIndex = left;
    for (int i = left; i < right; i++) {
        if (arr[i] <= pivot) {
            swap(arr, i, sortedIndex);
            sortedIndex++;
        }
    }
    swap(arr, sortedIndex, right);
    quickSort(arr, left, sortedIndex - 1);
    quickSort(arr, sortedIndex + 1, right);
}

private void swap(int[] arr, int i, int j) {
    int tmp = arr[i];
    arr[i] = arr[j];
    arr[j] = tmp;
}
```

## 참고

[Quicksort](https://en.wikipedia.org/wiki/Quicksort)<br>
[퀵 정렬](https://ko.wikipedia.org/wiki/%ED%80%B5_%EC%A0%95%EB%A0%AC)