---
title : "[프로그래머스] Lv.01 : 삼총사 (파이썬)"

categories:
  - Programmers

comments: true
share: false
classes: wide
use_math: true

toc: true
toc_label: "목차"

date: 2023-11-04
last_modified_at: 2023-11-04
---

# 🔎 난이도
> **Lv.01**


# ✏️ 문제
> <https://school.programmers.co.kr/learn/courses/30/lessons/131705>  

# ✒️ 문제 설명
한국중학교에 다니는 학생들은 각자 정수 번호를 갖고 있습니다.  
이 학교 학생 3명의 정수 번호를 더했을 때 0이 되면 3명의 학생은 삼총사라고 합니다.  
예를 들어, 5명의 학생이 있고, 각각의 정수 번호가 순서대로 $-2, 3, 0, 2, -5$ 일 때,  
첫 번째, 세 번째, 네 번째 학생의 정수 번호를 더하면 $0$ 이므로 세 학생은 삼총사입니다.  
또한, 두 번째, 네 번째, 다섯 번째 학생의 정수 번호를 더해도 $0$ 이므로 세 학생도 삼총사입니다.  
따라서 이 경우 한국 중학교에서는 두 가지 방법으로 삼총사를 만들 수 있습니다.  

한국중학교 학생들의 번호를 나타내는 정수 배열 $number$ 가 매개변수로 주어질 때,  
학생들 중 삼총사를 만들 수 있는 방법의 수를 $return$ 하도록 $solution$ 함수를 완성하세요.

<br>

# 🙅‍♂️ 제한사항
* $3$ $\le$ $number$ 의 길이 $\le$ $13$  

* $-1000$ $\le$ $number$ 의 각 원소 $\le$ $1000$  

* 서로 다른 학생의 정수 번호가 같을 수 있습니다.

# 🤖 입출력 예

|number|result
|:---:|:---:|
[-2, 3, 0, 2, -5] | 2
[-3, -2, -1, 0, 1, 2, 3] | 5
[-1, 1, -1, 1] | 0

# 🤖 입출력 예 설명
* 입출력 예 # 1  
  * 문제의 예시와 같습니다.

* 입출력 예 # 2
  * 학생들의 정수 번호 쌍 (-3, 0, 3), (-2, 0, 2), (-1, 0, 1), (-2, -1, 3), (-3, 1, 2) 이 삼총사가 될 수 있으므로, 5를 return 합니다.

* 입출력 예 # 3
  * 삼총사가 될 수 있는 방법이 없습니다.

<br>

# 🧐 아이디어
> number 리스트에서 3개의 원소를 뽑아 합이 0이되는 경우를 찾아 개수를 세는 문제였다.

<br>

# 📝 내 풀이
``` python

def solution(number):
    # 출력 및 정답
    answer = 0

    # 3중 반복문을 통해 number 원소 3개씩 뽑기
    for i in range(0, len(number)-2):
        for j in range(i+1, len(number)-1):
            for k in range(j+1, len(number)):
                # 원소 3개의 합이 0이라면, 즉, 삼총사라면 정답 += 1
                if (number[i] + number[j] + number[k]) == 0:
                    answer += 1
    return answer

```
<br>

# 😳 풀이 리뷰
처음에는 DFS로 구현하여 풀었지만, 코드도 직관적이지 못하였고, 다시 보니 이해하기도 어려웠다.  
그래서 삼중 반복문을 통해 원소 3개를 뽑는 것을 구현하였다.  
삼중 반복문보다 더욱 간단하게 푸는 법은 itertools의 combinations 라이브러리를 활용하는 방법이 있다.
~~~python
from itertools import combinations
~~~
