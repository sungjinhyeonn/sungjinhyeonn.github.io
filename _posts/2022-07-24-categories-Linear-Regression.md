---
title: "Linear Regression"
excerpt: "본문의 주요 내용을 여기에 입력하세요"

categories:
  - Categories1
tags:
  - [tag1, tag2]

permalink: /categories1/Linear-Regression/

toc: true
toc_sticky: true

Typora-root-url: ../

use_math: true

date: 2020-05-21
last_modified_at: 2021-10-09
---

# Linear Regression

![lec2-3](/assets/images/posts_img/2022-07-24-categories-Linear-Regression/lec2-3.jpg)

공부 시간에 따른 성적에 대한 데이터를 가지고 지도 학습을 한다고 가정한다.

사전에 수집한 성적이라는 **"정답"**이 존재하므로 "supervised learning"에 해당하며, 추정하고자 하는 값이 실수값이므로 regression problem이다. 여기에 성적과 공부 시간 사이에 선형의 관계가 존재한다고 가정하면 **Linear regression**이 되는 것이다.

# Hypothesis

**Hypothesis** 란, input (feature)과 output (target) 의 관계를 나타내는 함수이다.

선형 회귀에서는 다음과 같은 선형 함수를 자주 사용한다.

$$
H(x) = Wx + b
$$

우리의 목표는 여러가지 W와 b를 시도하여 평면 상에서 주어진 데이터 좌표들에 가장 잘 맞는, 혹은 그 점들을 가장 잘 대표하는 직선을 찾아내는 것이다.

# Cost function

우리가 세운 가설과 실제 데이터가 얼마나 다른지 판단하기 위해서 Cost function을 사용한다.

![1](/assets/images/posts_img/2022-07-24-categories-Linear-Regression/1.png)

M개의 데이터에 대해 우리가 예측한 값과 실제값의 차이를 제곱하여 데이터의 수로 나누어준다.

## cost funtion 일반화
