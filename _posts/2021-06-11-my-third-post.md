---
title:  "큰 수의 법칙(이코테)"
excerpt: "배열의 크기 N, 숫자가 더해지는 횟수 M, 최대 연속K번 더하기 가능"

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
author_profile: true
sidebar:
  nav: "[Greedy]"
---
주어진 조건으로는 N(2<=N<=1000), M(1<=M<=10000), K(1<=K<=10000)
배열의 크기 N, 숫자가 더해지는 횟수 M, 최대 연속K번 더하기 가능
따라서, 가장 큰수를 구하는 방법은 N의 리스트 중에서 가장 큰수를 K번 더하고 두번째로 큰수를 한번 더해주고 이 과정을 반복해주면 가장 큰 값이 도출된다.
```
n, m, k = map(int, input().split()) #n,m,k 각각 입력 받기
n_list = list(map(int, input().split())) #n에 해당되는 리스트 입력 받기

n_list.sort() #리스트를 크기 순으로 나열하기
fir = n_list[n-1] #제일 큰 수
sec = n_list[n-2] #두번째로 큰 수

sum = 0 #sum값 초기화

while True:
    for i in range(k): #제일 큰 수 k 번 더하기
        if m == 0: #m이 0일때 반복문 탈출
            break
        sum += fir
        m -= 1 #더하기 할 때 마다 m에서 1 빼주기
    if m == 0: #m이 0일때 반복문 탈출
        break
    sum += sec #두번째로 큰 수 한번 더해주기
    m -= 1 #더하기 할 때 마다 m에서 1 빼주기

print(sum)
```