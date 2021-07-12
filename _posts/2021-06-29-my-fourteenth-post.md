---
title:  "기준에 따라 데이터를 정렬"
excerpt: "여러가지 정렬 종류에 대해서 알아보자!"

categories:
  - Sort
tags:
  - [Algorithm, Sort]
toc: true
toc_sticky: true
date: 2021-06-29
last_modified_at: 2021-06-29
sitemap :
changefreq : daily
priority : 1.0
author_profile: true
sidebar:
  nav: "[Sort]"
---
#정렬

데이터를 특정한 기준에 따라서 순서대로 나열하는 것을 말한다.

#선택정렬

데이터가 무작위로 여러 개 있을 경우, 이중에 가장 작은 데이터를 선택한후 맨 앞에 있는 데이터와 치환하고 그 다음 작은 데이터를 앞에서 두번째 데이터와 치환하는 과정을 반복하게 되면 가장 작은 수부터 차례대로 정리가 된다.
이런 것을 선택정렬 알고리즘이라고 한다.

선택정렬의 예로는
```
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(len(array)):
    min_index = i #가장 작은 원소 인덱스
    for j in range(i + 1, len(array)):
        if array[min_index] > array[j]:
            min_index = j
    array[i], array[min_index] = array[min_index], array[i]

print(array)
```
```
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#삽입정렬

선택정렬과는 다르게 데이터를 하나씩 확인하면서 각 데이터를 적절한 위치에
삽입하는 방법이라고 보면 된다.

삽입정렬의 예로는
```
array = [7, 5, 9, 0, 3, 1, 6, 2, 4, 8]

for i in range(1, len(array)):
    for j in range(i, 0, -1): #인덱스 i 부터 1까지 감소하며 반복
        if array[j] < array[j-1]: #한 칸씩 왼쪽 이동
            array[j], array[j - 1] = array[j - 1], array[j]
        else: #자신보다 작은 수 만나면 멈춤
            break

print(array)
```
(삽입정렬은 항상 두 번째 데이터부터 시작한다.)

#퀵정렬

기준을 설정한 다음 큰 수와 작은 수를 교환한 후 리스트를 반으로 나누는 방식으로 동작한다. 이 때 반으로 나누는 기준을 피벗이라고 한다.

퀵정렬의 예로는
```
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array, start, end):
  if start >= end #원소가 1개인 경우 종료
    return
  pivot = start #피벗은 첫 번째 원소로 지정
  left = start + 1
  right = end
  while left <= right:
    #피벗보다 큰 수 찾을 때까지 반복
    while left <= end and array[left] <= array[pivot]:
      left += 1
    #피벗보다 작은 수 찾을 때까지 반복
    while right > start and array[right] >= array[pivot]:
      right -= 1
    if left > right: #엇갈리면 작은 수와 피벗 교체
      array[right], array[pivot] = array[pivot], array[right]
    else: #엇갈리지 않으면 작은 수와 큰 수 교체
      array[left], array[right] = array[right], array[left]
  #분할 이후 왼쪽과 오른쪽에서 각각 정렬 수행
  quick_sort(array, start, right-1)
  quick_sort(array, right + 1, end)

quick_sort(array, 0, len(array) - 1)
print(array)
```

파이썬의 장점을 살리면
```
array = [5, 7, 9, 0, 3, 1, 6, 2, 4, 8]

def quick_sort(array):
  #리스트에 하나 이하의 원소가 있으면 종료
  if len(array) <= 1:
    return array

  pivot = array[0] #피벗은 첫번째 수
  tail = array[1:] #피벗을 제외한 리스트

  left_side = [x for x in tail if x <= pivot] #분할된 왼쪽
  right_side = [x for x in tail if x > pivot] #분할된 오른쪽

  #분할 이후 왼쪽과 오른쪽에서 각각 정렬 후, 전체 리스트 반환
  return quick_sort(left_side) + [pivot] + quick_sort(right_side)

print(quick_sort(array))
```

#계수정렬

특정한 조건이 부합할 때만 사용할 수 있는 매우 빠른 정렬 알고리즘이다.
일반적으로 가장 큰 수와 가장 작은 수의 차이가 1,000,000을 넘지 않으면
효과적으로 사용할 수 있다.

계수정렬의 예로는
```
#모든 원소의 값이 0보다 크거나 같다고 가정
array = [7, 5, 9, 0, 3, 1, 6, 2, 9, 1, 4, 8, 0, 5, 2]
#모든 범위를 포함하는 리스트 선언(모든 값은 0으로 초기화)
count = [0] * (max(array) + 1)

for i in range(len(array)):
  count[array[i]] += 1 #각 데이터에 해댱하는 인덱스의 값 증가

for i in range(len(count)): #리스트에 기록된 정렬 정보 확인
  for j in range(count[i]):
    print(i, end = ' ') #띄어쓰기를 구분으로 등장한 횟수만큼 인덱스 출력
```
```
0 0 1 1 2 2 3 4 5 5 6 7 8 9 9
```