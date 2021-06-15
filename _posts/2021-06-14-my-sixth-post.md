---
title:  "아이디어를 코드로 바꾸는 구현(이코테)"
excerpt: "상하좌우 문제"

categories:
  - Realization
tags:
  - [Algorithm, Realization]
toc: true
toc_sticky: true
date: 2021-06-14
last_modified_at: 2021-06-14
sitemap :
changefreq : daily
priority : 1.0
---
구현에 대해서 간단하게 정리하자면 "머릿속의 알고리즘을 소스코드로 바꾸는 과정"으로 보면 된다.
구현은 크게 완전탐색과 시뮬레이션으로 나뉜다. 
완전탐색은 모든 경우의 수를 주저 없이 다 계산하는 해결 방법이며,
시뮬레이션은 문제에서 제시한 알고리즘을 한 단계씩 차례대로 직접 수행하는 것이다.

상하좌우 문제를 살펴보자

문제는 여행가 A가 N X M 크기의 정사각형 공간 위에 서 있다. 공간은 1 X 1 크기의 정사각형이고
가장 왼쪽위 좌표는 (1, 1)이며, 가장 오른쪽 좌표는 (N, N)이다. 시작좌표는 항상 (1,1)이다.

조건 중
L : 왼쪽으로 한 칸 이동
R : 오른쪽으로 한 칸 이동
U : 위로 한 칸 이동
D : 아래로 한 칸 이동

입력 조건은 공간의 크기를 나타내는 N(1<=N<=100), 여행가 A가 이동할 계획(1<=A<=100)
출력 조건은 A가 도착할 좌표를 공백으로 나타내면 된다.

입력 예시로
```
5
R R R U D D
```
따라서 코드를 작성해보면
```
n = int(input()) #정사각형 크기 값 입력받기
x, y = 1, 1 #초기 좌표값 설정
routes = input().split()

dx = [0, 0, -1, 1]
dy = [-1, 1, 0, 0]
way = ['L', 'R', 'U', 'D'] #L R U D에 따른 이동방향

for route in routes:
    for i in range(len(way)):
        if route == way[i]:
            nx = x + dx[i]
            ny = y + dy[i]
        #정사각형의 공간 벗어나는 것 제외
        if nx > n or ny > n or nx < 1 or ny < 1:
            continue

        x, y = nx, ny

print(x, y)
```