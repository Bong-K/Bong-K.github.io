---
title:  "왕실의 나이트(이코테)"
excerpt: "체스판의 나이트의 움직임을 계산해보자!"

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
체스판은 8 X 8의 좌표 평면이다.
나이트는 특정한 위치에서 다음과 같은 2가지 경우로 이동할 수 있다.
1. 수평으로 두 칸 이동한 뒤에 수직으로 한 칸 이동하기
2. 수직으로 두 칸 이동한 뒤에 수평으로 한 칸 이동하기
행을 1부터 8로 표현하고 열을 a부터 h로 표현하겠다.

나이트가 갈 수 있는 방향이라 봤자 모두 8가지 밖에 안된다.
```
location = input() #나이트 초기 위치 입력받기
side = int(location[1])
updown = int(location[0])

count= 0 #카운트 초기화

#나이트가 갈수 있는 모든 방향 정의
routes = [(1,2), (1,-2), (2,1), (2,-1) ,(-1,2), (-1,-2), (-2,1), (-2,2)]

for route in routes:
    #나이트의 초기 위치에서 다음 위치 지정해주기
    next_side = side + route[1]
    next_updown = updown + route[0]
    #나이트의 위치가 정사각형 안에 존재할 때 카운트 증가
    if next_side >= 1 or next_side <= 8 or next_updown >=1 or next_updown <=8:
        count += 1

print(count)
```