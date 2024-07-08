---
title: "프로그래머스 평행 문제: 정답률 53%"
layout: single
author_profile: true
tags:
  - coding-test
  - programmers
  - 평행
---
요약: 수학을 코드에 접목

# 코딩 테스트

- 코딩테스트 공부할 겸 레벨 0부터 차근차근 올라가는 중에 정답률 53%짜리 문제를 봤다.
- 문제를 풀기 위해 수학적 사고를 했던 부분이 재밌었다.
- 평행이란 어떤 것을 의미할까를 생각하다보니 논리적 사고력에 접근해서 푼 좋았던 무네

```python

def solution(dots):
    li = dots.pop()  # 기준이 되는 하나의 리스트를 빼준다.
    idx = 0
    answer = 0
    while True:
        if idx == len(dots):
            break
        dots_ = dots[:]
        list_ = dots_.pop(idx)
        answer = calc(li, list_) == calc(*dots_)
        if answer == 1:
            break
        idx += 1
    return answer


def calc(list1: list, list2: list):
    """
    평행이라 함은 기울기가 같다는 뜻이다. 그러므로 기울기를 구한 뒤 비교한다.
    y1 = ax1 + b
    y2 = ax2 + b

    y1 - y2 = ax1 - ax2
    a = (y1 - y2) / (x1 - x2)

    :param list1:
    :param list2:
    :return:
    """
    x1, y1 = list1
    x2, y2 = list2
    return (y1 - y2) / (x1 - x2)

```