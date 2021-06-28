---
title:  "음료수 얼려먹기(이코테)"
excerpt: "얼음틀의 모양이 주어졌을 때 생성되는 총 아이스크림의 개수를 구하자!"

categories:
  - Dfs&Bfs
tags:
  - [Algorithm, DFS&BFS]
toc: true
toc_sticky: true
date: 2021-06-25
last_modified_at: 2021-06-25
sitemap :
changefreq : daily
priority : 1.0
author_profile: true
sidebar:
  nav: "[DFS&BFS]"
---
N X M 크기의 얼음 틀이 있다. 구멍이 뚫려 있는 부분은 0, 칸이가 존재하는 부분은 1로 표시된다.
구멍이 뚫려 있는 부분끼리 상, 하, 좌, 우로 붙어 있는 경우 서로 연결되어 있는 것으로 간주한다. 이때 얼음 틀의 모양이 주어졌을 때 생성되는 총 아이스크림의 개수를 구하는 프로그램을 작성해 보아라.

입력조건
- 첫 번째 줄에 얼음 틀의 세로 길이 N과 가로 길이 M이 주어진다. (1<=N,M<=1000)
- 두 번째 줄부터 N+1번째 줄까지 얼음 틀의 형태가 주어진다.
- 이때 구멍이 뚫려있는 부분은 0, 그렇지 않은 부분은 1이다.

출력조건
- 한 번에 만들 수 있는 아이스크림의 개수를 출력해라.

앞서 말했던 DFS의 방식과 같이
1. 특정한 지점의 주변 상하좌우를 살펴본 뒤에 주변 지점 중에서 값이 '0'이고
   아직 방문하지 않은 지점이 있다면 해당 지점을 방문한다.
2. 방문한 지점에서 다시 상하좌우를 살펴보면서 방문을 다시 진행하면
   연결된 모든 지점을 방문할 수 있다.
3. 1,2 번 과정을 모든 노드에 적용시켜 방문하지 않은 지점의 수를 샌다.
```
#얼음 틀 크기 입력받기
n, m = map(int, input().split())

#2차원 리스트 입력받기
graph = []
for i in range(n):
    graph.append(list(map(int, input())))

#DFS로 특정한 노드를 방문한 뒤에 연결된 모든 노드들도 방문
def dfs(x, y):
    #주어진 범위를 벗어나는 경우 종료
    if x <= -1 or x>= n or y <= -1 or y >= m:
        return False
    #현재 노드를 아직 방문하지 않았다면
    if graph[x][y] == 0:
        #해당 현재 노드 방문 처리
        graph[x][y] = 1
        #상하좌우 위치 모두 재귀적 호출
        dfs(x - 1, y)
        dfs(x + 1, y)
        dfs(x, y - 1)
        dfs(x, y + 1)
        return True
    return False

#모든 위치에 대해 음료수 채우기
result = 0
for i in range(n):
    for j in range(m):
        #현재위치에서 dfs 수행
        if dfs(i, j) == True:
            result += 1

print(result)
```