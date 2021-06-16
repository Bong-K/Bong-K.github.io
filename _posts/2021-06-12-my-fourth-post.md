---
title:  "숫자 카드 게임(이코테)"
excerpt: "게임의 룰에 알맞게 카드를 뽑는 프로그램을 만들어보자!"

categories:
  - Greedy
tags:
  - [Algorithm, Greedy]
toc: true
toc_sticky: true
date: 2021-06-12
last_modified_at: 2021-06-12
sitemap :
changefreq : daily
priority : 1.0
---
게임을 이기는 방법은 여러개의 숫자 카드 중 가장 높은 숫자가 쓰인 카드 한 장을 뽑는 것이다.

조건
1. 숫자가 쓰인 카드들이 N 곱하기 M 형태로 놓여있다. 이때 N은 행, M은 열을 의미한다.
2. 먼저 뽑고자 하는 카드가 있는 행을 선택한다.
3. 그다음 선택된 행에 포함된 카드들 중 가장 숫자가 낮은 카드를 뽑는다.
4. 처음에 카드를 골라낼 행을 선택할 때, 이후에 해당 행에서 가장 숫자가 낮은 카드를 뽑을 것을 고려해 최종적으로 가장 높은 숫자를 뽑을 수 있도록 전략을 세우자.

이 조건들을 가장 간단하게 해석해보면 행에 있는 각 리스트에서 가장 작은수들 중 비교해서 큰수를 찾으면 되는 것이다.
```
n, m = map(int, input().split()) #n,m 값 입력 받기

result = 0 #결과 값 초기화 해주기

for i in range(n):
    n_list = list(map(int, input().split())) #각 행에 리스트 입력 받기
    min_value = min(n_list) #행에서 가장 작은 값 도출
    result = max(result, min(n_list)) #가장 작은 값들 중 큰수 지정

print(result) #결과 값 출력
```