---
title:  "탐색 알고리즘 DFS/BFS(이코테)"
excerpt: "DFS/BFS에 대해서 깊고 쉽게 알아보자!"

categories:
  - Dfs&Bfs
tags:
  - [Algorithm, DFS&BFS]
toc: true
toc_sticky: true
date: 2021-06-23
last_modified_at: 2021-06-23
sitemap :
changefreq : daily
priority : 1.0
author_profile: ture
sidebar:
  nav: "[DFS&BFS]"
---
DFS는 깊이 우선 탐색이라고 부르며, 그래프에서 가장 깊은 곳을 우선적으로 탐색하는 알고리즘이다.
DFS를 알기 위해서는 그래프의 기본 구조를 알아야 한다.
그래프는 노드와 간선으로 표현되며 이때 노드를 정점이라고도 말한다.
쉽게 말하면 노드와 노드를 연결하는 줄을 간선이라고 보면된다.
그래프는 크게 두가지 방식으로 표현한다.
![dfs bfs예제](https://user-images.githubusercontent.com/82932338/123071218-6eb82980-d44f-11eb-9d07-046b25f5c110.jpg)
이 그림에 대한 예를 들어보자!

인접 행렬 방식은 2차원 배열에 각 노드가 연결된 형태를 기록하는 방식이다.
(연결되어 있지 않은 노드끼리는 무한의 비용이라고 작성한다.)
```
INF = 999999999 #무한비용 선언

#2차원 리스트 이용해 인접 행렬 표현
```
graph =[
    [0, 7, 5],
    [7, 0, INF],
    [5, INF, 0]
]

print(graph)
```
```
[[0, 7, 5],[7, 0, 999999999], [5, 999999999, 0]]
```

인접 리스트 방식에서는 
모든 노드에 연결된 노드에 대한 정보를 차례대로 연결하여 저장한다.
```
#행이 3개인 2차원 리스트로 인접 리스트 표현
graph = [[] for _ in range(3)]

#노드 0에 연결된 노드 정보 저장(노드, 거리)
graph[0].append((1,7))
graph[0].append((2,5))

#노드 1에 연결된 노드 정보 저장(노드, 거리)
graph[1].append((0,7))

#노드 2에 연결된 노드 정보 저장(노드, 거리)
graph[2].append((0,5))

print(graph)
```
```
[[(1, 7), (2, 5)], [(0, 7), (0,5)]
```

인접 행렬 방식의 특징은 모든 관계를 저장해서 노드 개수가 많으면
많을 수록 메모리가 불필요하게 낭비되는데에 비해서 
인접 리스트 방식은 연결된 정보만을 저장하기 때문에 메모리를 
효율적으로 사용한다.

DFS에 대해서 설명을 해보자면
1. 탐색 시작 노드를 스택에 삽입하고 방문처리를 한다.
2. 스택의 최상단 노드에 방문하지 않은 인접 노드가 있으면
   그 인접 노드를 스택에 넣고 방문 처리를 한다.
   방문하지 않은 인접 노드가 없으면 스택에서 최상단 노드를 꺼낸다.
3. 2번의 과정을 더 이상 수행할 수 없을 때 까지 반복한다.
![image](https://user-images.githubusercontent.com/82932338/123082985-919c0b00-d45a-11eb-8a36-d91072a77907.png)
이 그림에 대한 코드를 짜보면
```
#DFS 메서드 정의
def dfs(graph, v, visited):
    #현재 노드 방문 처리
    visited[v] = True
    print(v, end=' ')
    #현재 노드와 연결된 다른 노드를 재귀적으로 방문
    for i in graph[v]:
      if not visited[i]:
        dfs(graph, i, visited)

#각 노드가 연결된 정보를 리스트 자료형으로 표현(2차원 리스트)
graph = [
  [],
  [2, 3, 8],
  [1, 7],
  [1, 4, 5],
  [3, 5],
  [3, 4],
  [7],
  [2, 6, 8],
  [1, 7]
]

#각 노드가 방문된 정보를 리스트 자료형으로 표현(1차원 리스트)
visited = [False] * 9

#정의된 DFS 함수 호출
dfs(graph, 1, visited)
```
```
1 2 7 6 8 3 4 5
```

BFS에 대해서 설명을 하면
1. 탐색 시작 노드를 큐에 삽입하고 방문 처리를 한다.
2. 큐에서 노드를 꺼내 해당 노드의 인접 노드 중에서 방문하지 않은
   노드를 모두 큐에 삽입하고 방문 처리를 한다.
3. 2번의 과정을 더 이상 수행할 수 없을 때까지 반복한다.

DFS에서의 똑같은 그림으로 코드를 짜보면
```
from collections import deque

#BFS 메서드 정의
def bfs(graph, start, visited):
  #큐 구현을 위해 deque 라이브러리 사용
  queue = deque([start])
  #현재 노드를 방문 처리
  visited[start] = True
  #큐가 빌 때까지 반복
  while queue:
    #큐에서 하나의 원소를 뽑아 출력
    v = queue.popleft()
    print(v, end=' ')
    #해당 원소와 연결된, 아직 방문하지 않은 원소들을 큐에 삽입
    for i in graph[v]:
      if not visited[i]:
      queue.append(i)
      visited[i] = True

#각 노드가 연결된 정보를 리스트 자료형으로 표현(2차원 리스트)
graph = [
  [],
  [2, 3, 8],
  [1, 7],
  [1, 4, 5],
  [3, 5],
  [3, 4],
  [7],
  [2, 6, 8],
  [1, 7]
]

#각 노드가 방문된 정보를 리스트 자료형으로 표현(1차원 리스트)
visited = [False] * 9

#정의된 BFS 함수 호출
bfs(graph, 1, visited)
```
```
1 2 3 8 7 4 5 6
```