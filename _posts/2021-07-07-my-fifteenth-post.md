---
title:  "위에서 아래로"
excerpt: "수열을 내림차순으로 정렬하는 프로그램을 만들어라!"

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
큰 수부터 작은 수의 순서롤 정렬하는 내림차순을 만들어보아라.

입력조건
-첫째 줄에 수열에 속해 있는 수의 개수 N이 주어진다.(1 <= N <= 500)
-둘째 줄부터 N + 1번째 줄까지 N개의 수가 입력된다. 수의 범위는 1이상
 100,000 이하의 자연수 이다.

출력조건
-입력으로 주어진 수열이 내림차순으로 정렬된 결과를 공백으로 구분하여
 출력한다. 동일한 수의 순서는 자유롭게 출력해도 괜찮다.

```
#n입력받기
n = int(input())

#N개의 정수를 입력받아 리스트에 저장
array = []
for i in ragne(n):
    array.append(int(input()))

#파이썬 기본 정렬 라이브러리 이용해 정렬 수행
array = sorted(array, reverse=True)

#정렬 수행 결과 출력
for i in array:
    print(i. end=' ')
```

코드를 간결하게 쓸 수 있는 기본 정렬 라이브러리를 이용하는 것이 효과적이다.