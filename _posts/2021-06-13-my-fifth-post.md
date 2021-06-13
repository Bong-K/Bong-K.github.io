---
title:  "1이 될 때까지(이코테)"
excerpt: "어떠한 수 N이 1이 될 때까지 두가지 과정중 하나를 반복적 선택하여 수행!"

categories:
  - Greedy
tags:
  - [Algorithm, Greedy]
toc: true
toc_sticky: true
date: 2021-06-13
last_modified_at: 2021-06-13
---
문제는 N과 K가 주어질 때 N이 1이 될 때까지 1번 혹은 2번의 과정을 수행해야 하는 최소 횟수를 구해라

조건은
1. N에서 1을 뺀다.
2. N을 K로 나눈다.
3. N(2<=N<=100000), K(2<=K<=100000), N은 항상 K보다 크거나 같다.

이 문제를 해결하기 위해서 떠오르는 방법은 "최대한 많이 나누기"이다.
```
n, k = map(int, input().split()) #n, k의 값 입력받기

result = 0 #결과 값 초기화

while n >= k:
    while n % k != 0: #n이 k로 나누어 떨어지지 않을때 n에서 1씩 빼주기
        n -= 1
        result += 1
    
    n //= k #k로 나누어주기
    result += 1

while n > 1: #n이 1보다 클때 1씩 빼주기
    n -= 1
    result += 1

print(result) #결과 값 도출
```