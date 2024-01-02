# Linear_Algebra
- This repository is written and practiced while studying linear algebra.
- Learning resource
  - Lecture Video
    - 인공지능을 위한 선형대수, 고려대학교 주재걸 교수님 - https://www.boostcourse.org/ai251
    - 선형대수학1, 세종대학교 하길찬 교수님 - http://www.kocw.net/home/cview.do?cid=f41a378321625410
  - Book
    - Lay et al. Linear Algebra and Its Applications, 5th edition, 2015
    - HOWARD ANITON. 알기 쉬운 선형대수 제 12판(한티에듀)
- Current modified: 12/28/2023 Thu.

# Contents
- Elements in linear algebra - finished
- Linear system - in progress
- Linear combination, vector equation, Four views of matrix multiplication
- Linear independence, span, and subspace
- Linear transformation
- Least squres
- Eigendecomposition
- Singular value decomposition

## Learning Notes
### 1. Elements in linear algebra(선형대수의 요소들)
- 스칼라(scalar): 하나의 수 e.g., 3.8
- 벡터(vector): 순서가 정해져 있는 일종의 배열(array), 일반적으로 열벡터로 나타내고 굵은 소문자로 나타냄 ↔ 순서가 정해져 있지 않은 것은 집합(set)
  - 행벡터(row vector): 행렬에서 각 행의 값들로 이루어진 벡터 e.g., [1, 2, 3, 4]
  - 열벡터(column vector): 행렬에서 각 열의 값들로 이루어진 벡터 ~ 행벡터를 세로로 쓰면 열벡터
  - Column은 기둥이라는 뜻이 있는데, verticacl한 이미지를 상상하면 행과 열이 헷갈리지 않음
  - n차원의 벡터는 일반적으로 열벡터로 나타냄
  - 따라서, 행벡터는 일반적으로 전치(transpose)를 써서 나타냄. Transpose of x(=xᵀ)
- 행렬(matrix): 2차원 숫자 배열, 대문자로 나타냄
  - 행렬의 크기: 3x2(3 by 2)는 3개의 행과 2개의 열로 이루어진 행렬이라는 뜻
- 행렬의 표기법
  - A(nxn): 정사각행렬(square matrix), 행렬의 행의 개수와 열의 개수가 같은 행렬(#rows = #columns)
  - A(mxn): 직사각행렬(rectangular matrix), 정사각행렬이 아닌 행렬, 즉 행렬의 행의 개수와 열의 개수가 다른 행렬
  - Aᵀ: 행렬의 전치, 주대각 성분들을 기준으로 행렬을 회전
  - Aij: i번째 행, j번째 열의 요소
  - Ai,: - i번째 행벡터
  - A:,j - j번째 열벡터
- 벡터 & 행렬의 덧셈과 곱셈
  - 덧셈은 같은 크기일 때만 가능하며, 각 위치의 요소들을 합하면 됨
  - 스칼라배 곱셈도 가능함
  - 3x2 크기의 A 행렬과 2x2 크기의 B 행렬이 있을 때, 두 행렬의 곱 AB는 3x2 크기의 행렬이 나온다.
    - 이때, 앞에 있는 행렬의 열의 크기와 뒤에 있는 행렬의 행의 크기가 동일해야만 곱 연산이 가능하다.
    - 만약 2x3의 크기의 A 행렬과 2x2 크기의 B 행렬을 곱하면(AB) 크기가 같지 않으므로 연산할 수 없다.
    - 또한, AB와 BA는 완전 다른 연산인데, 이를 통해 교환법칙이 성립하지 않는다는 것을 알 수 있다.(NOT commutative)
    - 같은 크기의 두 정사각행렬을 곱했을 때 AB와 BA 모두 연산이 가능한 경우가 있는데 이 경우에도 일반적으로 연산 결과는 같지 않다.
- 기타 법칙
  - A(B + C) = AB + AC: 분배법칙이 성립한다(distributive).
  - A(BC) = (AB)C: 결합법칙이 성립한다(associative).
  - (AB)ᵀ = BᵀAᵀ: AB를 전치(transpose)하면 A와 B의 순서가 바뀐다.
  - (AB)^-1 = B^-1A^-1: 전치와 마찬가지로 AB의 역행렬은 순서가 바뀐다.
### 2. Linear System(선형방정식)
- 선형 방정식(lienar equation): x1, x2, ..., xn의 미지수가 있을 때 미지수를 풀기 위한 방정식으로 a1x1 + a2x2 + ... + anxn = b 와 같이 표기한다.
  - 위 방정식의 표기법을 선형대수에서는 aᵀx = b로 간결하게 표기한다.
  - a1, a2, ..., an를 계수(coefficient)라고 하고 실수나 복소수이며 이미 알고 있는 경우가 일반적이다.
  - b는 상수(constant)라고 한다.
  - x1, x2, ..., xn과 같이 한개의 미지수 혹은 미지수의 집합을 포함하고 있는 방정식 선형방정식(linear system)이라 한다.
- 선형방정식은 머신러닝에서 input data를 통해 target data의 가중치를 구하고자할 때 활용된다.
  - e.g., 사람의 키(x1), 몸무게(x2), 흡연 여부(x3)를 통해 수명을 구하고자 할 때 사용
  - 60x1 + 5.5x2 + 1x3 = 66
  - 65x1 + 5.0x2 + 0x3 = 74
  - 55x1 + 6.0x2 + 1x3 = 78
  - 위와 같은 연립방정식을 아래와 같이 계수의 집합 행렬 A, 미지수의 열벡터 x, 상수의 열벡터 b로 나타내어 Ax = b와 같이 표기할 수 있다.
  - Ax = b에서 x를 구하기 위해서 A의 역행렬을 구하여 좌변과 우변에 곱하면 AA^-1 = I(항등행렬) 이므로, x=bA^-1로 구할 수 있다.
- 항등행렬(identity matrix)
  - 항등행렬을 정사각행렬이면서 대각성분이 모두 1이고 나머지 요소는 모두 0인 행렬을 뜻한다.
  - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/9392ec3a-f092-4eb2-b2ed-54affa159d56)
  - 항등행렬이라는 이름 그대로 항등행렬 I는 어떠한 한 행렬 A와 곱하더라도 그 값이 A가 나온다. xIn = x
- 역행렬(inverse matrix)
  - 역행렬은 정사각행렬에서만 존재한다.
    - 직사각행렬이라면 행 축소(row reduction)와 같은 방법으로 근사값을 계산할 수 있음(Book Chap 1.2, 1.5 추가 학습)
  - AA^-1 = A^-1A = In
    - 역행렬은 기존 행렬의 곱하는 위치와 상관없이 항상 결과는 항등행렬이 나온다.
  - 역행렬을 통해 선형방정식을 해결하는 방법: 역행렬을 구해서 역행렬에 상수 벡터인 b를 곱하면 해를 구할 수 있음!
    - 1. Ax = b
      2. A^-1Ax = A^-1b
      3. Inx = A^-1b
      4. x = A^-1b
  - 2x2 크기의 역행렬은 공식으로 빠르게 구할 수 있음. 이보다 더 큰 크기의 역행렬을 구하고 싶다면, 가우시안 소거법(gaussian elimination)을 활용하면 빠르게 역행렬을 구할 수 있음
- 행렬식(determinant)
  - 행렬식은 행렬이 가역적인지 비가역적인지 판별하는 식이다. 예를 들어, 2x2 행렬 A가 있다면 det A = bc-ad이다.
  - det A ≠ 0이라면 A는 invertible하다고 표현하고, det A = 0이라면 non-invertible하다고 표현한다.
  - 어떠한 행렬 A가 가역적(invertible)이면 그 해는 항상 자명하다(uniquely obtained). - 즉, 해가 오직 하나이다.
  - 비가역적(non-invertible)인 행렬이라면, 해가 무수히 많거나(infinitely many solutions) 해가 없다(no solution).
    - 해가 무수히 많은 경우(under-determined system): 계수들의 비율이 같은데, 상수값도 같아 0x + 0y = 0과 같이 나오는 경우
      - 머신러닝을 예로 들면, data(방정식)보다 feature(미지수)가 더 많은 경우 - 방정식이 미지수보다 적은 경우
    - 해가 없는 경우(over-determined system): 계수들의 비율이 같은데 상수값이 달라 0x + 0y = 2와 같이 나오는 경우
      - 머신러닝을 예로 들면, feature(미지수)보다 data(방정식)이 더 많은 경우 - 방정식이 미지수보다 많은 경우
  - 추가 학습자료
    - https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/resources/lecture-18-properties-of-determinants/
    - https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/resources/lecture-19-determinant-formulas-and-cofactors/

## Theories
- 정리1. 직사각행렬을 축소된 행사다리꼴 행렬로 만들면 단 하나의 기약 행사다리꼴 행렬만 갖는데, 즉, 다른 기약 행사다리꼴은 존재하지 않는다.(Lay p.13)

---
### References
1) https://m.blog.naver.com/kiseop91
