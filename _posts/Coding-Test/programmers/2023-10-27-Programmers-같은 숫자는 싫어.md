---
title : "[프로그래머스] Lv.01 : 같은 숫자는 싫어 (파이썬)"

categories:
  - Programmers

comments: true
share: false
classes: wide

toc: true
toc_label: "목차"

date: 2023-10-27
last_modified_at: 2023-10-27
---

# 🔎 난이도
> **Lv.01**


# ✏️ 문제
> <https://school.programmers.co.kr/learn/courses/30/lessons/12906>  

# ✒️ 문제 설명
배열 arr가 주어집니다. 배열 arr의 각 원소는 숫자 0부터 9까지로 이루어져있습니다.  
이때, 배열 arr에서 연속적으로 나타나는 숫자는 하나만 남기고 전부 제거하려고 합니다.  
단, 제거 된 후 남은 수들을 반환할 때는 배열 arr의 원소들의 순서를 유지해야 합니다.  

* arr = [1, 1, 3, 3, 0, 1, 1] 이면 [1, 3, 0, 1] 을 return 합니다.
* arr = [4, 4, 4, 3, 3] 이면 [4, 3]을 return 합니다.

배열 arr 에서 연속적으로 나타나는 숫자는 제거하고 남은 수들을 return 하는 solution 함수를 완성해 주세요.

<br>

# 🙅‍♂️ 제한사항
* 배열 arr의 크기 : 1,000,000 이하의 자연수
* 배열 arr의 원소의 크기 : 0보다 크거나 같고 9보다 작거나 같은 정수


# 🤖 입출력 예

|arr|answer
|---|---|
[1, 1, 3, 3, 0, 1 ,1] | [1, 3, 0, 1]
[4, 4, 4, 3, 3] | [4, 3]

# 🤖 입출력 예 설명
* 입출력 예 # 1,2 문제의 예시와 같습니다.


<br>

# 🧐 아이디어
단순히 연속된 숫자의 중복을 제거하는 문제였다면, Set 자료형을 통해 손 쉽게 풀 수 있었을 겁니다. 하지만 기존에 제시한 배열 arr의 순서를 보장해야하기 때문에 Set 자료형을 쓸 수 없습니다.
~~~python
example = [1,1,6,6,2,2,3,3,3,4,5,5]

set_example = set(example)
print(set_example)
# {1, 2, 3, 4, 5, 6}
~~~

순서 보장을 위해 원래 배열 그대로 탐색을 하며 answer 리스트에 arr 배열의 첫 번째 값(인덱스 = 0)을 넣어 준 후, 1부터 마지막 인덱스까지 전 후 값을 비교하여 다르다면 answer의 append 해주는 방법으로 풀었습니다.

<br>

# 📝 내 풀이
``` python
def solution(arr):
    answer = [arr[0]] # arr의 첫 번째 원소
    for i in range(1,len(arr)): # 1 ~ arr의 길이 만큼 반복 (길이가 n이라면 n-1 반복)
        if arr[i] != arr[i-1]: # arr배열의 전,후 값 비교 (1,0) (2,1) (3,2) ...
            answer.append(arr[i]) # 같지 않다면 answer 리스트에 원소 추가
    return answer
```
<br>

# 😳 다른 풀이
~~~python
def diff_solution(arr):
    answer = []
    for i in arr:
        if answer[-1:] != [i]:
            answer.append(i)
    return answer
~~~

answer의 마지막 원소와 현재 i와 비교를 하며 같지 않을 경우, 즉, 중복되지 않을 경우 answer 리스트에 원소를 추가하는 방법입니다.