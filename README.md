# Linear_Algebra
- This repository is written and practiced while studying linear algebra.
- Learning resource
  - Lecture Videos
    - 인공지능을 위한 선형대수, 고려대학교 주재걸 교수님 - https://www.boostcourse.org/ai251
    - 선형대수학1, 세종대학교 하길찬 교수님 - http://www.kocw.net/home/cview.do?cid=f41a378321625410
  - Books
    - Lay et al. Linear Algebra and Its Applications, 5th edition, 2015
    - HOWARD ANITON. 알기 쉬운 선형대수 제 12판(한티에듀)
    - Mike X Cohen. 개발자를 위한 실전 선형대수학
- Current modified: 01/24/2024 Wed.

# Contents
- Elements in linear algebra - completed
- Linear system - in progress
- Linear combination, vector equation, Four views of matrix multiplication - in progress
- Linear independence, span, and subspace - completed
- Linear transformation
- Least squres
- Eigendecomposition
- Singular value decomposition

## Learning Notes
### 1. Elements in linear algebra(선형대수의 요소들)
- 스칼라(scalar): 하나의 수 e.g., 3.8
- 벡터(vector, v): 순서가 정해져 있는 일종의 배열(array), 일반적으로 열벡터로 나타내고 굵은 소문자로 나타냄 ↔ 순서가 정해져 있지 않은 것은 집합(set)
  - 기하학적 해석: 특정 길이(크기)와 방향(각도)을 가진 직선
    - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/a236f174-b372-4a8c-803c-3c93b83d60a0)
  - 벡터의 차원(dimensionality): 벡터가 가진 원소의 수, e. g., R²: 두 개의 원소가 있는 벡터
    - R0: 영차원 부분공간 (차원 = 0)
    - Rn: n차원 공간 (차원 = n)
    - n차원 벡터: n개의 원소를 갖는 벡터 = n 순서쌍(n-tuple)
  - 벡터의 방향(orientation): 벡터가 열 방향인지 행 방향인지를 나타냄(n차원의 벡터는 일반적으로 열벡터로 나타냄)
    - 열벡터(column vector): 행렬에서 각 열의 값들로 이루어진 벡터 ~ 행벡터를 세로로 쓰면 열벡터
      - Column은 기둥이라는 뜻이 있는데, verticacl한 이미지를 상상하면 행과 열이 헷갈리지 않음
    - 행벡터(row vector): 행렬에서 각 행의 값들로 이루어진 벡터 e.g., [1, 2, 3, 4]
      - 행벡터는 일반적으로 전치(transpose)를 써서 나타냄. Transpose of x(=xᵀ)
  - 영벡터(zero vector): 모든 원소가 0인 벡터
  - Practice
    <pre>
      x = [ [1], [4], [5], [6] ]라면, x는 4차원 열벡터, x ∈ R⁴
      y = [ [.3], [-7] ]라면, y는 2차원 열벡터, y ∈ R²
      z = [ [1, 4, 5, 6] ]라면, z는 4차원 행벡터, z ∈ R⁴
      * x와 z는 동일한 순서로 동일한 원소를 갖고 있지만 방향이 다르기 때문에 다른 벡터임을 주의
    </pre>
    <img width="243" alt="스크린샷 2024-01-16 오후 2 52 57" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/762c64f4-2b9b-4b43-80b3-9c5ec5f6505a">
- 행렬(matrix, M): 2차원 숫자 배열(벡터를 한 차원 더 끌어올린 것), 굵은 대문자로 나타냄
  - 데이터 과학에서는 행렬을 관측 데이터가 있는 행과 특징(feature) 열을 가진 데이터 테이블로 간주함
  - 행렬의 크기: 3x2(3 by 2)는 3개의 행과 2개의 열로 이루어진 행렬이라는 뜻
- 행렬의 표기법
  - A(nxn): 정사각행렬(square matrix), 행렬의 행의 개수와 열의 개수가 같은 행렬(#rows = #columns)
  - A(mxn): 직사각행렬(rectangular matrix), 정사각행렬이 아닌 행렬, 즉 행렬의 행의 개수와 열의 개수가 다른 행렬
  - Aᵀ: 행렬의 전치, 주대각 성분들을 기준으로 행렬을 회전
    - 열벡터를 행벡터로 변환하거나 행벡터를 열벡터로 변환함
    - 중요! 벡터를 두 번 전치하면 벡터는 원래 방향이 됨. (Aᵀ)ᵀ = A
      - 당연한 것 같지만 AI에서 중요한 증명에서 핵심 근거가 됨.
  - Aij: i번째 행, j번째 열의 요소
  - Ai,: - i번째 행벡터
  - A:,j - j번째 열벡터
- 특수 행렬
  - 난수 행렬(random number matrix): 가우스(정규) 분포 등으로부터 무작위로 추출된 숫자를 가진 행렬(선형대수학을 코드로 공부할 때 유용, 임의의 크기와 계수(rank)로 쉽고 빠르게 생성 가능하기 때문)
  - 정방 행렬(square matrix)과 비정방 행렬(nonsquare matrix)
    - 정방 행렬: 행 수와 열 수가 같은 행렬. 즉,  R(N*N) 행렬
    - 비정방 행렬: 행 수와 열 수가 다른 행렬, 행 수 > 열 수: '높다'고 표현, 행 수 < 열 수: '넓다'고 표현
  - 대각 행렬(diagonal matrix)
    - 모든 비대각 원소가 0이며, 대각 원소는 0이거나 0이 아닌 값을 가진 행렬(NumPy의 diag() 함수)
      - 행렬의 대각(diagonal)은 왼쪽 위에서 시작해서 오른쪽 아래로 대각선 방향으로 내려가는 원소들
    - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/b640c675-80f8-494e-940b-d22b5dd44626)
  
  - 삼각 행렬(triangular matrix)
    - 주 대각선(main diagonal)의 위 또는 아래가 모두 0인 행렬(NumPy의 triu() 함수는 상삼각 행렬, tril() 함수는 하삼각 행렬을 추출하는 함수)
    - 상삼각 행렬: 0이 아닌 원소가 대각선 위에 있는 행렬
      - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/a83d46ab-65fe-4059-bafd-b83c85430512)

    - 하삼각 행렬: 0이 아닌 원소가 대각선 아래에 있는 행렬
      - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/6220e95c-ac0a-4fe3-9713-065f287d0126)

  - 단위 행렬(unit matrix)
    - 가장 중요한 행렬로써 모든 대각 원소가 1인 정방 대각 행렬, 대문자 I로 나타냄(NumPy의 eye() 함수를 사용해서 생성)
      - 행렬 또는 벡터에 단위 행렬을 곱하면 자기 자신과 동일한 행렬 또는 벡터가 된다는 점에서 숫자 1과 동등함
    - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/cac5288d-e3bd-48e1-803e-da543a379b9b)

  - 영 행렬
    - 영벡터와 유사하게 모든 원소가 0인 행렬, 굵은 체를 사용하여 0으로 나타냄(NumPy의 zeors() 함수를 사용해서 생성)
- 벡터 & 행렬의 덧셈과 곱셈
  - 덧셈은 동일한 차원을 갖는 벡터끼리만 연산이 가능하며, 서로 대응되는 원소끼리 합하면 됨
  - 벡터의 덧셈과 뺄셈의 기하학적 해석: 삼각형 법칙, 평행사변형 법칙
    - 특히, 벡터의 뺄셈은 직교벡터 분해의 기초이며 선형 최소제곱법의 기초가 되기 때문에 아주 중요한 개념
  - ![이코테 - 0 4](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/ddb96c39-470e-4fce-bedb-ab6930015d56)

  - 행렬 이동(shifting a matrix) - 행렬의 고윳값을 찾는 메커니즘과행렬을 정규화하는 메커니즘으로 응용
    - 정방 행렬에 스칼라를 더하는 방식으로 단위 행렬에 스칼라를 곱해서 더하는 방식으로 구현
      <pre>
        A = np.array([ [4, 5, 1], [0, 1, 11], [4, 9, 7] ]
        s = 6
        A + s * np.eye(len(A))
      </pre>
    - 데이터 과학에서는 행렬의 수치적 안정성을 높이고 이동의 효과를 보면서 행렬의 가능한 많은 정보를 보존하기 위해 상대적으로 적은 양을 이동
  - 스칼라배 곱셈도 가능(아주 간단함, 각 벡터나 행렬의 원소에 스칼라를 곱하면 됨). denote by α, β, λ, ... ~ e. g., λw = [36, 16, 4] (λ = 4, w = [9, 4, 1].T)
    - 스칼라-벡터 곱셈의 기하학적 해석(행렬 공간, 고유벡터, 특이벡터에서 중요한 해석)
      - 벡터의 방향은 변경하지 않으면서 크기만 조정
        - but, 스칼라가 음수일 때는 벡터 방향이 뒤집힘(=회전된 벡터), 회전된 벡터도 여전히 무한한 선을 가리키므로 방향을 바꾼 것이 아님
      - <img height="200" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/d6364d0e-9bf4-4b4c-920c-1c033b0c8b9a" />


- 표준 행렬 곱셈(matrix multiplication) - 다른 행렬 곱셈들(e.g., 아다마르곱 등)과 구분하기 위해 표준 행렬 곱셈이라 함
  - 행렬 곱셈: 왼쪽 행렬의 행과 오른쪽 행렬의 열 사이의 모든 쌍에 대한 선형 관계를 저장하는 행렬
  - 행렬 곱셈 유효성에 관한 규칙
    - '내부' 차원의 수가 일치할 때만 유효하고 곱셈 행렬의 크기는 '외부' 차원의 수로 정의
      - 내부 차원의 수가 일치할 때만 유효한 이유: 곱셈 행렬의 (i, j)번째 원소가 왼쪽 행렬의 i번째 행과 오른쪽 행렬의 j번째 열 사이의 내적이기 때문
        - 내적: 두 벡터 사이의 관계를 인코딩한 숫자
    - e.g., 3x2 크기의 A 행렬과 2x2 크기의 B 행렬이 있을 때, 두 행렬의 곱 AB는 3x2 크기의 행렬이 생성
      - 이때, 앞에 있는 행렬의 열의 크기와 뒤에 있는 행렬의 행의 크기가 동일해야만 곱 연산이 가능
      - 만약 2x3의 크기의 A 행렬과 2x2 크기의 B 행렬을 곱하면(AB) 크기가 같지 않으므로 연산할 수 없음
      - 또한, AB와 BA는 완전 다른 연산인데, 이를 통해 교환법칙이 성립하지 않는다는 것을 알 수 있다.(NOT commutative)
      - 같은 크기의 두 정사각행렬을 곱했을 때 AB와 BA 모두 연산이 가능한 경우가 있는데 이 경우에도 일반적으로 연산 결과는 같지 않음
    - Practice
      - <img width="450" alt="스크린샷 2024-01-16 오후 3 04 52" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/6b9baba4-63e8-4e52-9aa8-feefec498295">
      
        - 차원이 일치하지 않으면 연산할 수 없음, but NumPy에는 브로드캐스팅 연산이 있어서 행벡터와 열벡터 덧셈이 가능함
        - <img width="400" alt="스크린샷 2024-01-16 오후 3 34 44" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/1973e665-d1b9-488f-8744-433d024e4aae">

- 행렬과 벡터 곱셈
  - 표준 행렬 곱셈과 동일한 메커니즘으로 행렬과 벡터 곱셈의 결과는 항상 벡터. 데이터 과학, 머신러닝 등 많은 곳에서 사용됨
  - 행렬-벡터 곱셈은 행렬 공간의 기저
  - 행벡터가 아닌 열벡터만 행렬의 오른쪽에 곱할 수 있고 열벡터가 아닌 행벡터만 행렬의 왼쪽에 곱할 수 있음
  - 행렬에 행벡터를 곱하면 행벡터가 생성되고 열벡터를 곱하면 열벡터가 생성됨
    - 즉, Av 및 vᵀA는 유효하지만 Avᵀ 및 vA는 유효하지 않음(행벡터는 오직 왼쪽, 열벡터는 오직 오른쪽만 가능)
      - MxN 크기의 행렬과 1xM 크기의 행벡터를 곱할 수 없지만 1xM 크기의 행벡터에 MxN 크기의 행렬을 곱하면 결과로 1xN 크기의 행벡터가 나옴
      - 역으로, MxN 크기의 행렬과 Nx1 크기의 열벡터를 곱하면 Mx1의 열벡터가 나와서 연산이 가능하지만 Nx1 크기의 열벡터에 MxN크기의 행렬을 곱하는 것은 불가능
  - 행렬-벡터 곱셈의 두 가지 구체적인 해석
    1. 선형 가중 결합
    2. 기하학적 변환 
- 벡터 크기와 단위 벡터(Norm and Unit vector)
  - 벡터의 크기(norm, 기하학적 길이): 벡터의 꼬리부터 머리까지의 거리. denoted by || v ||
    - 일반적으로 표준 유클리드(euclidean) 거리 공식으로 구함(L2 norm)
    - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/d153c4ea-9d59-4827-871e-9479d28f194f)
  - 단위벡터(unit vector): 기하학적인 길이가 1인 벡터, || v || = 1
    - 직교 행렬과 회전 행렬, 고유벡터, 특이벡터에 활용
    - 단위벡터 생성(벡터의 정규화): 벡터를 벡터 노름으로 나누면 단위벡터(v^)가 생성된다.
      - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/b8517561-7069-49f2-9389-3f534fcd14a5) ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/874430d5-ea98-4926-880e-aad41b92e6af)
- 벡터의 내적(dot product, scalar product), 선형대수학 전체에서 가장 중요한 연산
  - 합성곱(convolution), 상관관계(correlation), 푸리에 변환(Fourier transform), 행렬 곱셈, 선형 특징 추출, 신호 필터링 등 많은 연산과 알고리즘의 기본
  - denoted by vᵀw (otherwise, v·w or < v, w >)
  - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/20b51d68-1943-4af0-8843-204ef447c45e)
    - 두 벡터에서 대응되는 원소끼리 곱한 다음 모든 결과를 더함(즉, 원소별로 곱하고 합하는 것)
      - 동일한 차원의 두 벡터 사이에서만 성립
  - Practice
    - [1 2 3 4]·[5 6 7 8] = 5 + 12 + 21 + 32 = 70
    - <img width="237" alt="스크린샷 2024-01-16 오후 4 00 55" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/e51d3628-d00f-4eec-8711-a054e9c09497"> <img width="241" alt="스크린샷 2024-01-16 오후 4 04 52" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/b188c063-3cdc-4e85-8bc4-5ca720b1d28c">
    - 내적의 흥미로운 특성: 벡터에 스칼라를 곱하면 내적도 그만큼 커짐(s*v = σvᵀw), 음수 스칼라를 곱하면 기호가 반대로 되며 0을 곱하면 내적도 0이 됨
  - 즉, 내적은 두 벡터 사이의 유사성(similarity) 또는 매핑(mapping)의 척도로 해석할 수 있음
    - ex: 20명의 키와 몸무게를 수집하여 두 개의 벡터에 저장했다면 두 변수들은 서로 관련이 있다고 예상할 수 있음(키가 큰 사람이 더 무거운 경향이 있음)
      - 따라서 위와 같이 서로 관련이 있으면 두 벡터의 내적은 클 것
      - 그런데, 그램(g)과 센티미터(cm)로 측정된 데이터의 내적은 단위의 차이로 인해 킬로그램(kg)과 미터(m)로 측정된 데이터의 내적보다 큼.
        - 이러한 단위의 차이는 정규화 계수로 제거할 수 있음
  - 두 변수 사이의 정규화된 내적: 피어슨 상관계수(pearson correlation coefficient)
  - 내적의 분배 법칙
    - aᵀ(b+c) = aᵀb + aᵀc
      - <img width="327" alt="스크린샷 2024-01-16 오후 4 12 45" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/4ad15f3b-f418-42b7-9c57-4188ed2d1c33">
  - 내적의 기하학적 해석: 두 벡터의 노름(크기)를 곱하고 두 벡터 사이의 각도에서 코사인값만큼 크기를 늘린 것
    - α = cos(θv, w) ||v|| ||w||, (-1 <= cos(θv, w) <= +1)
    - ![이코테 - 0](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/dd3167bc-d2a3-4c44-b65d-3c8eca48f2cb)

    - 암기: 직교벡터의 내적은 0이다. (아래 3개 내용 모두 동일한 내용, 반복해서 읽고 암기)
      - 두 벡터가 직교한다.
      - 두 벡터는 내적이 0이다.
      - 두 벡터 사이의 각은 90°이다.

- 그 외 벡터 곱셈
  - 아다마르곱(hardamard product)
    - 차원이 같은 두 벡터에 대해서 서로 대응되는 각 원소를 곱하는 방법 ~ 곱의 결과는 같은 차원의 벡터
      - 여러 스칼라의 곱을 곱할 때 편리함
    - <img width="245" alt="스크린샷 2024-01-16 오후 4 22 12" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/25555bd6-40ed-415d-8122-437af0020e3a">

  - 외적(outer product): rank-1 행렬(계수-1 행렬)
    - 열벡터와 행벡터를 이용해 행렬을 만듦. denoted by vwᵀ
    - ![이코테 - 0 2](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/4176104e-6d50-4942-a7d5-1145068b614c)
      - 외적 행렬의 각 행은 행벡터 스칼라에 대응되는 열벡터 원소를 곱한 것
      - 외적 행렬의 각 열은 열벡터 스칼라에 대응되는 행벡터 원소를 곱한 것

- 직교벡터 분해
  - 벡터 또는 행렬을 '분해'하면 여러 간단한 조각으로 나뉘어짐
    - 숨겨진 정보를 밝혀내거나 행렬을 사용하기 쉬운 형태로 만들거나 데이터를 압축하기 위해 사용
    - 그람-슈미트 과정(Gram-Schmidt Process), QR 분해와 직접적인 연관이 있음
  - 직교 투영법(orthogonal projection) = 최소 거리 투영 ~ 벡터 분해를 배우기 위해 꼭 필요한 기초 내용
    <img height="300px" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/2fa44aca-f961-4cbe-9918-43919bae5d3a">
  
    - 표준 위치에 두 벡터 a, b가 있을 때, a에서 b의 머리와 최대한 가까운 점을 찾아야 함
    - 즉, 투영 거리가 최소가 되도록 벡터 b를 벡터 a에 투영. 그 점은 a의 크기를 줄인 βa가 됨
    - 중요한 것은 벡터 뺄셈을 통해 b에서 βa까지의 선을 정의할 수 있음
    - b-βa가 βa와 직교한다 = 이 벡터들은 수직. 즉, 두 벡터 사이의 내적이 0
      - aᵀ(b - βa) = 0
        1. aᵀb - βaᵀa=0 (내적의 분배 법칙)
        2. βaᵀa = aᵀb
        3. ∴ β = aᵀb / aᵀa
    - 직교 투영법(orthogonal projection): β = aᵀb / aᵀa
      - 최소제곱식, 통계학, 머신러닝 등의 많은 분야에서 기초가 됨
  - 직교벡터 분해: '목표벡터' t와 '기준벡터' r이 있을 때, 목표벡터를 두 개의 다른 벡터로 분해하는 것
    1. 두 벡터의 합은 목표벡터
    2. 하나의 벡터는 기준벡터와 직교하지만 다른 벡터는 기준벡터와 평행
    - 목표벡터로부터 만들어진 두 벡터는 수직 성분 t⊥r, 평행 성분 t||r
    <img height="300px" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/643c8524-733a-4e47-b06d-85f36f7d3e54">
    
    1. 평행 성분 t||r 찾는 방법: r과 평행한 벡터는 t를 r에 투영한 것
       - t||r = r(tᵀr / rᵀr)
    2. 수직 성분 t⊥r 찾는 방법: 목표벡터 t에서 평행 성분 t||r을 뺀 것(두 성분의 합이 목표 벡터가 된다는 것을 활용)
      - t = t⊥r + t||r
      - ∴ t⊥r = t - t||r

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

### 3. Linear combination, vector equation, Four views of matrix multiplication(선형 결합, 벡터 방정식, 행렬 곱셈을 바라보는 4가지 관점)
- 벡터 집합(vector space): 벡터들의 모음.(유한하거나 무한한 수의 벡터가 존재) denoted by V = { v1, ..., vn }
- 선형 결합(linear combination): 여러 변수마다 가중치를 다르게 주어 정보를 혼합하는 방법
  - w = λ1v1 + λ2v2 + ... + λnvn (즉, 스칼라와 벡터를 곱한 후 값들을 합하는 것을 선형 결합이라고 함)
  - 선형 종속적(linearly dependent): 벡터 집합 V에서 적어도 하나의 벡터를 집합의 다른 벡터들의 선형 결합으로 나타낼 수 있을 때 벡터 집합을 선형 종속적(linearly dependent)이라고 함
  - <img width="400" alt="스크린샷 2024-01-19 오후 2 03 25" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/b8f9fd41-c621-4020-a1f7-405fc86e8043">
    
  - 선형 결합 응용 분야
    1. 통계 모델로부터 예측된 데이터는 최소제곱 알고리즘을 통해 계산되는 회귀변수(독립변수)와 계수(스칼라)의 선형 결합으로 생성됨
    2. 차원 축소 과정(e.g., 주성분 분석)에서 각 성분(인자 또는 모드)은 성분의 분산을 최대화하는 가중치(계수)와 데이터 채널의 선형 결합으로 도출됨
    3. 인공 신경망(ANN)에는 입력 데이터의 선형 결합과 비선형 변환의 2가지 연산이 있음. 가중치(w)는 비용 함수(loss function)을 최소화하도록 학습됨
       - 비용 함수(loss function): 모델 예측과 실제 목표 변수 사이의 차이
- 벡터 방정식
- 행렬 곱셈을 바라보는 4가지 관점
    
### 4. Linear independence, span, and subspace(선형 독립성, 생성, 부분공간)
- 선형 독립적(linearly independent): 집합에 있는 벡터들의 선형 결합으로 집합의 아무런 벡터도 나타낼 수 없을 때 벡터 집합을 '선형 독립적(linearly independent)'이라고 함 ↔ 선형 종속적(linearly dependent)
  - <img width="400" alt="스크린샷 2024-01-19 오후 2 22 18" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/e2b392a8-2c47-456f-b772-b43c89c3e636">

  - 위의 경우는 집합 내의 벡터의 수가 적어서 선형 배수로 나타낼 수 있는지 없는지를 눈으로만 계산하여도 쉽게 선형 종속적인지 선형 독립적인지 판단할 수 있음. 하지만 아래와 같이 훨씬 복잡한 벡터 집합이라면?
    - <img width="400" alt="스크린샷 2024-01-19 오후 2 24 42" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/047480f0-9cbb-4b7b-91f4-b27ad514e704">
     
      - 선형 독립성을 결정하는 방법은 벡터 집합으로 행렬을 만들고 행렬의 계수(rank)를 계산한 다음 행의 수와 열의 수 중에서 더 작은 값과 비교하면 됨. 이는 차후에 학습하고 정리할 예정
  - 수학에서의 선형 독립성: 벡터를 선형적으로 결합해서 영벡터를 생성할 수 있는 방법이 없다면 벡터 집합은 선형 독립적
    - 선형 종속의 수학적 정의
      - 0 = λ1v1 + λ2v2 + ... + λnvn, λ ∈ R, λ1 ≠ 0  
      - λ1 ≠ 0이며 자명하지 않은 해(nontrivial solution)가 존재. 즉, 벡터 집합이 선형 종속적이라면 선형 결합으로 영벡터를 만들 수 있다는 뜻.
- 부분공간(subspace): (유한한) 벡터 집합의 벡터들을 사용하여 수많은 다른 가중치를 사용해 무한히 선형 결합하여 만든 공간(벡터 집합으로 생성된 결과)
  - 벡터 집합에서 생성되는 부분공간의 차원은 선형 독립 집합을 형성하는 데 필요한 최소한의 벡터 수
  - 벡터 집합이 선형 독립적일 때: 부분 공간의 차원 = 집합의 벡터수
  - 벡터 집합이 선형 종속적일 때: 부분 공간의 차원 < 집합의 벡터수
- 생성(span): 가능한 모든 선형 결합을 구성하는 메커니즘
- 기저(basis): 행렬의 정보(e.g., 데이터)를 설명하는 데 사용하는 기준의 집합. 즉, 벡터 공간을 생성하는데 필요한 최소한의 벡터들을 나타냄(마인크래프트에서 건물을 지을 때 사용되는 블록들과도 같음)
  - 기저는 데이터 과학과 머신러닝에서 매우 중요(모든 분석은 본질적으로 특정 문제에 대한 최적의 기저벡터를 찾는 것이 목적이기 때문에)
  - 가장 일반적인 기저 집합: 데카르트 좌표계(Cartesian Coordinate System)
  - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/5fcd438c-2c82-42aa-bbef-f7a58953c977)

  - <img width="350" alt="스크린샷 2024-01-19 오후 2 49 49" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/6513f825-cbf0-4ed4-96ed-a52f0eb3e277">

    - 위는 2차원과 3차원 데카르트 그래프의 기저 집합으로 '표준 기저 집합'이라고 함(데카트르 기저 집합은 서로 직교하며 단위 길이인 벡터로 이루어져 있음)
    - <img width="298" alt="스크린샷 2024-01-19 오후 2 52 20" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/13cf88d0-ae8d-4d6d-a8cf-c89e8fd30bd6">
 
      - 표준 기저 집합이 유일한 기저 집합은 아님. 위의 T는 R2의 또 다른 기저 집합임
    
    - ![이코테 - 0 5](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/a1ac1200-2d7b-49b4-ae2f-7158b2de5cf9)      

      - 위 예제에서 S와 T는 모두 동일한 부분공간을 생성함. 하지만 S보다는 T를 더 선호함.(간결하고 직관적이기 때문)
  - 기저의 정의
    - 생성(span)과 독립성(independency)를 결합한 것(벡터 집합이 특정 부분공간을 생성하고 독립적인 벡터 집합이라면 해당 부분공간의 기저임)
 
## Summarization
- 벡터는 열 또는 행에 숫자를 나열한 것으로 순서가 중요. 벡터의 원소 수는 차원이라고 함. 벡터는 차원과 동일한 수의 축을 가진 기하학적 공간에서 하나의 선으로 나타낼 수 있음.
- 덧셈, 뺄셈, 아다마르곱과 같은 벡터 산술 연산은 원소별로 계산함.
- 내적은 차원이 같은 두 벡터 간의 관계를 인코딩한 단일 숫자로, 원소별로 곱하고 합해서 구함(내적은 매우 중요. 내적은 유사도와 관련이 있음).
- 두 벡터가 직교하면 내적은 0이며 기하학적으로 벡터가 직각으로 만나는 것을 의미함(분해에 활용).
- 직교벡터 분해는 하나의 벡터를 기준벡터와 직교하는 벡터, 평행한 벡터로 나누는 것임(공식은 기하학적으로 도출 가능하나, 공식이 내포한 개념인 '크기에 대한 매핑'을 기억해야 함).
- 벡터 집합은 벡터들의 모음이며, 벡터 집합에는 유한하거나 무한한 수의 벡터가 존재함.
- 선형 결합은 집합의 벡터들에 스칼라를 곱하고 합하는 것으로 선형대수학에서 가장 주요한 개념임.
- 집합에서 하나의 벡터가 집합의 다른 벡터들의 선형 결합으로 기술될 수 있으면 해당 벡터 집합은 선형 종속적임. 만약 이러한 선형 결합이 없다면 벡터 집합은 선형 독립적임.
- 부분공간은 벡터 집합의 가능한 모든 선형 결합으로 만들어진 무한 집합임.
- 기저는 공간을 측정하기 위한 일종의 자와 같은 개념임. 벡터 집합이 (1) 어떤 부분공간을 생성하고 (2) 선형 독립적이라면 해당 부분 공간에 대한 기저가 됨. 데이터 과학의 주요 목표는 데이터 집합을 설명하거나 문제를 해결하기 위한 최상의 기저 집합을 찾는 것임.

## Theories
- 정리1. 직사각행렬을 축소된 행사다리꼴 행렬로 만들면 단 하나의 기약 행사다리꼴 행렬만 갖는데, 즉, 다른 기약 행사다리꼴은 존재하지 않는다.(Lay p.13)

## Vector applications
- 상관관계
  - 상관관계는 통계와 머신러닝에서 가장 근본적이면서 중요한 분석 방법, 변수의 크기로 정규화된 두 변수 사이의 내적
    - 상관계수(correlation coefficient): 두 변수 사이의 선형 관계를 정량화한 숫자(-1(음의 상관관계)부터 +1(양의 상관관계) 사이의 범위)
    - 상관계수가 기대하는 범위 -1 ~ +1 사이에 존재하려면 정규화(normalization)가 필요
      1. 각 변수의 평균중심화: 각 데이터값에서 평균값을 빼는 것
      2. 피어슨 상관계수(벡터 노름 곱으로 내적을 나누기)
        - 피어슨 상관계수 전체 공식
          - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/9fc9e86d-0474-4c24-b102-7b482ffd2e83)

        - 선형대수학 용어로 나타낸 피어슨 상관계수(내적 표기법을 사용, x~는 x를 평균중심화한 것)
          - 아래 공식은 변수를 평균중심화된 것으로 가정하고 단순화한 것이라는 사실을 꼭 기억해야 함
          - ![이코테 - 0 6](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/1e80a181-0906-4bc1-83b8-5ece9bf63c47)

- 코사인 유사도
  - 상관관계와 유사하게 두 변수 간의 유사성을 평가하는 다른 방법
  - 내적의 기하학적 공식(α = cos(θA, B) ||A|| ||B||, (-1 <= cos(θA, B) <= +1))으로 코사인 항을 구한 것(α는 A와 B의 내적)
    - ![image](https://github.com/PSLeon24/Linear_Algebra/assets/59058869/27807d0f-03b7-4a6c-b8ad-1ff2e3cf4551)

- 상관관계와 코사인 유사도 차이
  - 피어슨 상관관계의 관점에서는 한 쪽 변수에 의해 다른 변수가 변한다면 변수 간의 숫자 차이는 결과에 영향을 미치지 않음
  - 코사인 유사도의 관점에서는 한 쪽 변수에 의해 다른 변수가 변한다면 변수 간의 숫자 차이가 결과에 영향을 미침

- 시계열 필터링과 특징 탐지
  - 필터링은 본질적으로 특징 탐지 기법
    - 템플릿(커널)이 시계열 신호의 일부와 일치하는 특징을 찾음(특정 기준에 최적화되도록 커널을 구성, e.g., 매끄러운 변동, 날카로운 에지, 특정 파형 모양)
    - 이렇게 필터링된 결과는 또 다른 시계열이 되어 이를 통해 신호의 특성이 커널의 특성과 얼마나 일치하는지 알 수 있음
  - 커널과 시계열 신호 사이의 내적을 계산하는 것이 필터링 메커니즘
    - 커널과 동일한 길이의 짧은 데이터 조각과 커널 사이의 내적을 계산, 이 과정으로 필터링된 신호 구간에서 한 점이 생성되고 커널을 오른쪽으로 한 구간씩 이동시키면서 다른 신호 조각과 내적을 계산해 나감
      - 이 과정을 합성곱(Convolution)이라고 함
      - <img height="300" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/f499c643-cf1f-4c5f-bdd8-d945801933a7">

- k-평균 클러스터링
  - k-평균 클러스터링: 그룹 중심까지의 거리를 최소화하도록 다변량 데이터를 상대적으로 적은 수(k)의 그룹 또는 범주로 분류하는 비지도 기법
  - 알고리즘
    1. 데이터 공간에서 임의의 k개 클러스터 중심점을 초기화(이때, 중심은 클래스 또는 범주, 다음 단계에서는 각 데이터 관측치를 각 클래스에 할당)
    2. 각 데이터 관측치와 각 중심 사이의 유클리드 거리를 계산
       - 하나의 데이터 관측치와 중심 사이의 유클리드 거리를 계산할 때 선형대수학 개념을 사용함  
    3. 각 데이터 관측치를 가장 가까운 중심의 그룹에 할당(이중 for문 대신 벡터와 브로드캐스팅을 사용하여 효율적으로 수행 가능)
    4. 각 중심을 해당 중심에 할당된 모든 데이터 관측치의 평균으로 갱신
    5. 수렴 기준을 만족할 때까지 또는 N회까지 2~4단계를 반복
    - <img height="300" alt="스크린샷 2024-01-24 오전 11 07 23" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/44f7f577-6d88-4563-97cb-157e8979ba94"> <img height="300" alt="스크린샷 2024-01-24 오전 11 07 13" src="https://github.com/PSLeon24/Linear_Algebra/assets/59058869/4d71825d-ae6a-48f4-8f0c-8216193e6d5f">

  
---
### References
1) https://m.blog.naver.com/kiseop91
