---
title:  "성적이 낮은 순서로 학생 출력하기"
excerpt: "각 학생의 이름과 정보를 토대로 성적 낮은 순으로 배열해라!"

categories:
  - Sort
tags:
  - [Algorithm, Sort]
toc: true
toc_sticky: true
date: 2021-07-10
last_modified_at: 2021-07-10
sitemap :
changefreq : daily
priority : 1.0
author_profile: true
sidebar:
  nav: "[Sort]"
---
* 입력조건

- 첫 번째 줄에 학생의 수 N이 입력된다.(1 <= N <= 100,000)
- 두 번째 줄부터 N + 1번째 줄에는 학생의 이름을 나타내는 문자열 A와 학생의 
  성적을 나타내는 정수B가 공백으로 구분되어 입력된다.
  문자열A의 길이와 학생의 성적으 100이하의 자연수이다.

* 출력조건

- 모든 학생의 이름을 성적이 낮은 순서대로 출력한다. 성적이 동일한 학생들의
  순서는 자유롭게 출력해도 괜찮다.

```
#N입력받기
n = int(input())

#N명의 학생정보를 입력받아 리스트 저장
array = []
for i in range(n):
  input_data = input().split()
  #이름은 문자열 그대로, 점수는 정수형으로 변환해 저장
  array.append((input_data[0], int(input_data[1])))

#키를 이용해 점수를 기준으로 정렬
array = sorted(array, key=lamda student: student[1])

#정렬 결과 출력
for student in array:
  print(student[0], end=' ')
```