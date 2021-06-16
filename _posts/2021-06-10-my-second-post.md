---
title:  "거스름돈 문제(이코테)"
excerpt: "500원, 100원, 50원, 10원 동전 무제한 존재/거슬러줘야 할 돈 N원 동전의 최소개수 구하기!"

categories:
  - Greedy
tags:
  - [Algorithm, Greedy]
toc: true
toc_sticky: true
date: 2021-06-10
last_modified_at: 2021-06-10
sitemap :
changefreq : daily
priority : 1.0
---
그리디 문제의 해결법은 '현재 상황에서 지금 당장 좋은 것만 고르는 방법"이며 문제와 같은 상황에서는 '가장 큰 동전 단위' 부터 돈을 거슬러주는 것이다.
```
N = int(input()) #N원 설정해주기
count = 0 #거슬러줄 동전 갯수 초기화

coins = [500, 100, 50, 10] #동전 종류 리스트 나열 

for coin in coins: #for문으로 반복
    count += N // coin #주어진 수 N을 coin으로 나눌때 마다 count 추가
    N %= coin #N을 코인으로 나눈 후 의 나머지

print(count)
```