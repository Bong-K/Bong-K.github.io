---
title:  "게임 개발(이코테)"
excerpt: "캐릭터가 맵 안에서 움직이는 시스템을 개발해보자! "

categories:
  - Realization
tags:
  - [Algorithm, Realization]
toc: true
toc_sticky: true
date: 2021-06-16
last_modified_at: 2021-06-16
sitemap :
changefreq : daily
priority : 1.0
author_profile: true
sidebar:
  nav: "[Realization]"
---
캐릭터가 있는 장소는 1 X 1크기의 정사각형으로 이루어진 N X M 크기의 직사각형으로, 각각의 칸은 육지 또는 바다이다.(캐릭터는 동서남북중 한곳을 본다.)
맵의 칸은 (A, B)로 나타낼 수 있고, A는 북쪽으로부터 떨어진 칸의 개수, B는 서쪾으로부터 떨어진 칸의 개수이다.
캐릭터는 상하좌우로 움직일 수 있고, 바다로 되어 있는 공간은 갈 수 없다.

1. 현재 위치에서 현재 방향을 기준으로 왼쪽 방향(반시계 방향으로 90도 회전한 방향)부터 차례대로 갈 곳을 정한다.
2. 캐릭터의 바로 왼쪽 방향에 아직 가보지 않은 칸이 없다면, 왼쪽 방향으로 회전한 다음 왼쪽으로 한 칸을 전진한다.
   왼쪽 방향에 가보지 않은 칸이 없다면, 왼쪽 방향으로 회전만 수행하고 1단계로 돌아간다.
3. 만약 네 방향 모두 이미 가본 칸이거나 바다로 되어 있는 칸인 경우에는, 바라보는 밯ㅇ향을 유지한 채로 한 칸 뒤로 가고 1단계로 돌아간다.
   이때 뒤쪽 방향이 바다인 칸이라 뒤로 갈 수 없는경우에는 움직임을 멈춘다.

* 입력조건
- 첫째 줄에 맵의 세로 크기 N과 가로 크기 M을 공백으로 구분하여 입력한다.
  (3<=N,M<=50)
- 둘째 줄에 게임 캐릭터가 있는 칸의 좌표(A,B)와 바라보는 방향 d가 각각 
  서로 공백으로 구분하여 주어진다.
  방향 d 값으로는 4가지가 존재한다. -0: 북쪽/ -1: 동쪽/ -2: 남쪽/ -3:서쪽
- 셋째 줄부터 맵이 육지인지 바다인지에 대한 정보가 주어진다. N개의 줄에 
  맵의 상태가 북쪽부터 남쪽순서대로, 각 줄의 데이터는 서쪽부터 동쪽 순서대로 주어진다. 맵의 외곽은 항상 바다로 되어있다. -0: 육지/ -1: 바다
- 처음에 캐릭터가 위차한 칸의 상태는 항상 육지이다.
```
n, m = map(int, input().split()) #맵의 크기 설정
x, y, look = map(int, input().split()) #캐릭터의 초기 위치 및 바라보는 방향

map = [] #맵의 상태 입력 받기
for i in range(n):
    map.append(list(map(int, input().split())))

#북동남서 방향 정의
dx = [-1, 0, 1, 0]
dy = [0, 1, 0, -1]

look_count = 0 #바라보는 방향 초기값
count = 1 #캐릭터가 초기 위치한 땅부터 세주므로 1로 시작
map[x][y] = '1' #캐릭터 초기 위치할 때 1이라고 정의해주기

while True:
    #바라보는 방향 왼쪽으로 회전할때 정의
    look -= 1
    if look == -1:
        look = 3
    #다음 이동 방향 정의
    nx = x + dx[look]
    ny = y + dy[look]
    #방향전환후 가보지 않은 칸이 존재할 경우
    if map[nx][ny] == 0:
        map[nx][ny] = '1'
        x, y = nx, ny
        count += 1
        look_count = 0
        continue
    #방향전환후 정면에 칸이 없거나 바다일때
    else:
        look_count += 1
    #네 방향 모두 못갈 때
    if look_count == 4:
        nx = x - dx[look]
        ny = y - dy[look]
        #뒤로 갈 수 있을 때 이동하기
        if map[nx][ny] == 0:
            x, y = nx, ny
        #뒤로도 못가는 경우 일때
        else:
            break
        look_count = 0

print(count)
```