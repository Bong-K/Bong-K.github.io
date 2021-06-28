---
title:  "아이디어를 코드로 바꾸는 구현(이코테)"
excerpt: "시각"

categories:
  - Realization
tags:
  - [Algorithm, Realization]
toc: true
toc_sticky: true
date: 2021-06-15
last_modified_at: 2021-06-15
sitemap :
changefreq : daily
priority : 1.0
author_profile: true
sidebar:
  nav: "[Realization]"
---
```
정수 N이 입력되면 00시 00분 00초부터 N시 59분 59초까지의 모든 시각 중에서 3이 하나라도 포함되는
모든 경우의 수를 구하는 프로그램을 작성하시오.

이 문제를 푸는 방법은 모든 경우의 수를 살펴보는 완전탐색을 구현하면된다.

일단 제일 먼저 든 생각은 저 시각을 문자열처럼 나열하면 쉽지 않을까?였다.
24 X 60 X 60으로 생각해보자
```
n = int(input()) #n의 값 입력 받기
count = 0 #count값 초기화

for i in range(n+1): #시간
    for j in range(60): #분
        for k in range(60): #초
            #문자열로 만들어 3을 찾는다.
            if '3' in str(i) + str(j) + str(k): 
                count += 1

print(count)
```