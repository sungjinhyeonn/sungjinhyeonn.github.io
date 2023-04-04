---
title: "벨만 방정식"
excerpt: "벨만 기대 방정식과 최적 방정식"

categories:
  - Categories2
tags:
  - [tag1, tag2]

permalink: /categories2/Bellman-Expectation-Equation/

toc: true
toc_sticky: true

Typora-root-url: ../

use_math: true

date: 2023-04-02
last_modified_at: 2023-04-02




---



# 벨만 방정식

## 벨만 기대 방정식

벨만 기대 방정식은 현재 상태의 가치함수와 다음 상태의 가치함수 사이의 관계를 식으로 나타낸 것이다.

$$
\begin{aligned}
v_\pi(s_t)&=E_\pi[G_t]
\\
&=E_\pi[r_{t+1} +{\gamma}r_{t+2}+{\gamma}^2r_{t+3}+..]
\\
&=E_\pi[r_{t+1}+\gamma(r_{t+2}+{\gamma}r_{t+3}+..)]
\\
&=E_\pi[r_{t+1}+{\gamma}G_{t+1}]
\\
&=E_\pi[r_{t+1}+{\gamma}v_\pi(s_{t+1})]
\end{aligned}
$$

상태 가치함수와 액션 가치 함수

$$
v_\pi(s) = \sum_{a\in A}\pi(a|s)q_\pi(s,a)
\\
q_\pi(s,a)=r_s^a+\gamma\sum_{s'\in S}P_{ss'}^av_\pi(s')
$$

대입하면

$$
v_\pi(s) = \sum_{a\in A}\pi(a|s)(r_s^a+\gamma\sum_{s'\in S}P_{ss'}^av_\pi(s'))
\\
q_\pi(s,a)=r_s^a+\gamma\sum_{s'\in S}P_{ss'}^a\sum_{a\in A}\pi(a'|s')q_\pi(s',a')
$$

### 보상 함수 $r_s^a$

각 상태에서 액션을 선택하면 얻는 보상

### 전이 확률 $p_{ss'}^a$

각 상태에서 액션을 선택하면 다음 상태가 어디가 될지에 관한 확률 분포

보상함수와 전이확률은 환경의 일부이다. 이 두가지를 알때를 MDP를 안다고 표현한다

전이 확률은 안다고 구체적으로 어느 상태에 도달하는지는 알 수 없고 샘플링을 해봐야한다.

### 모델-프리

MDP를 모를때 학습하는 접근법

### 모델 기반 혹은 플래닝

MDP를 아는 상황에서 실제로 경험해보지않고 머릿속에서 시뮬레이션을 해보는 학습

## 벨만 최적 방정식

MDP가 주어졌을 때 그 MDP 아에 존재하는 모든 $\pi$ 들 중에서 가장 좋은 $\pi$를 선택하여 계산한 최적 밸류

$$
v_* =\underset{\pi}{max}\;v_\pi (s)
\\
q_*(s,a) = \underset{\pi}{max}\;q_\pi (s,a)
$$

모든 상태에서 최적 밸류를 갖게하는 정책 $\pi_*$가 최소한 1개 이상 존재한다.

모든 상태에 대해 어떤 정책보다도 높은 밸류를 얻게되는 것을 최적 정책이라고 부른다.

### 부분순서

상태마다 정책의 좋음이 다를 수 있는데 이러한 상황에서 정책중에서 어떤 것이 좋다고 말하기 어렵다.

이러한 상황을 부분 순서라고 하며 전체 중에 일부만 대소관계를 비교하여 순서를 정할 수 있다

> MDP 내의 모든 $\pi$ 에 대해 $\pi_* > \pi$ 를 만족하는 $\pi_*$ 가 반드시 존재한다.
> 

### 최적 밸류와 최적의 액션 밸류 등식

- 최적의 정책 : $\pi_*$초
- 최적의 밸류 : $v_*(s) = v_{\pi_*}(s)$  ($\pi_*$를 따랐을 때의 밸류)
- 최적의 액션 밸류 : $q_*(s,a) = q_{\pi_*}(s,a)$ $(\pi_*$를 따랐을 때의 액션 밸류)

### 밸만 최적 방정식

$$
v_*(s) = \underset{a}{max}E[r+\gamma v_*(s') | s_t =s ,a_t=a]
\\
q_*(s,a) = E[r+\gamma \underset{a}{max}q_*(s',a')|s_t=s,a_t=a]
$$

상태 s 에서 한 스텝만큼 진행하여 보상을 받고 , 다음 상태인 s’ 의 최적 밸류를 더해준다.

밸만 기대 방정식 $E_\pi$에서 $\pi$ 가 사라진 이유는 값을 가장 크게 하는 액션 a를 선택하면 되기 때문에 정책의 역할은 사라진다.

$$
v_* =\underset{\pi}{max}\; q_*(s,a)
\\
q_*(s,a) = r_s^a +\gamma \sum_{s' \in S} P_{ss'}^a v_*(s')
$$

대입하여 정리하면

$$
v_* =\underset{\pi}{max} [r_s^a +\gamma \sum_{s' \in S} P_{ss'}^a v_*(s')]
\\
q_*(s,a) = r_s^a +\gamma \sum_{s' \in S} P_{ss'}^a \underset{\pi}{max}\; q_*(s,a)
$$