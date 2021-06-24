---
title:  "꼭 필요한 자료구조 기초(이코테)"
excerpt: "자료구조에 대해서 깊고 쉽게 알아보자!"

categories:
  - Dfs&Bfs
tags:
  - [Algorithm, DFS&BFS]
toc: true
toc_sticky: true
date: 2021-06-22
last_modified_at: 2021-06-22
sitemap :
changefreq : daily
priority : 1.0
---
탐색은 "많은 양의 데이터 중에서 원하는 데이터를 찾는 과정"이다.
DFS와 BFS가 있는데 이를 이해하기 위해서는 재귀함수와 스택과 큐를 알아야 한다.

자료구조는 "데이터를 표현하고 관리하고 처리하기 위한 구조"이며
기초 개념으로는 스택과 큐가 있다.

스택은 선입후출 구조 또는 후입선출 구조라고 불린다.

스택예제로
```
stack = []
stack.append(5)
stack.append(2)
stack.append(3)
stack.append(7)
stack.pop()
stack.append(1)
stack.pop()

print(stack)
print(stack[::-1])
```
결과는
```
[5, 2, 3, 1]
[1, 3, 2, 5]
```
가 나온다.

append()는 리스트의 가장 뒤쪽에 삽입하는 것이고
pop()는 리스트의 가장 뒤쪽에서 빼내는 것이다.

큐는 선입선출 구조로 불린다.

큐 예제로
```
from collections import deque

queue = deque() #큐 구현을 위해 deque 라이브러리 사용

queue.append(5)
queue.append(2)
queue.append(3)
queue.popleft()
queue.append(1)

print(queue)
queue.reverse()
print(queue)
```
결과는
```
deque([2, 3, 1])
deque([1, 3, 2])
```

재귀함수란 자기 자신을 다시 호출하는 함수이다.

재귀함수 호출로
```
def recursive_function():
  print('재귀 함수')
  recursive_function()

recursive_function()
```
계속 반복되다가 오류 메세지를 출력하고 멈출 것이다. 이 오류는 재귀의 최대 깊이를 초과했다는 내용이다.
따라서, 종료 조건을 명시해줘야지 함수가 무한히 호출 되지 않는다.
재귀함수 초반에 등장하는 if문이 종료 조건 역할을 수행한다.
```
def recursive_function(i):
  if i == 100
    return
  print(i, '번째 재귀 함수에서', i + 1, '번째 재귀 함수를 호출합니다.')
  recursive_function(i + 1)
  print(i, '번째 재귀 함수를 종료합니다.')

recursive_function(1)
```

재귀함수 예로는 팩토리얼 문제가 있는데 2가지 방식으로 살펴보면
```
#반복적 구현 n!
def factorial_interactive(n):
  result = 1
  #1부터 n까지의 수를 차례대로 곱하기
  for i in range(1, n+1):
    result *= i
  return result

#재귀적으로 구현한 n!
def factorial_recursive(n):
  if n <= 1: #n이 1 이하인 경우 1를 반환
    return 1
  #n! = n * (n-1)!로 코드 작성하기
  return n * factorial_recursive(n-1)
```