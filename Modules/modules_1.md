# Module

## 모듈의 정의

### 모듈

- 한 파일로 묶인 변수와 함수의 모음
- 특정한 기능을 하는 코드가 작성된 파이썬 파일(.py)
- 다른 프로그래머가 만들어 둔 변수나 함수들의 모음을 ‘모듈’이라고 함

### 모듈 예시

- math 내장 모듈
    - 파이썬이 미리 작성해 둔 수학 관련 변수와 함수가 작성된 모듈
    
    ```python
    import math
    
    print(math.pi) # 3.141592653589793 ...
    
    print(mate.sqrt(4)) # 2.0 
    ```
    

## 모듈 활용

### import 문 사용

- 같은 이름의 함수가 여러 모듈에 있을 때 충돌을 방지할 수 있음
- `.`(dot) 연산자
    - 점의 왼쪽 객체에서 점의 오른쪽 이름을 찾으라는 의미
- 단점
    - 자칫 코드가 길어질 수 있음
    - → 명시도가 높기 때문에 크게 단점이라고 보기 어렵긴 함

### from 절 사용

- 코드가 짧고 간결해짐

```python
from math import pi, sqrt

print(pi) # 변수명
print(sqrt(4)) # 함수명
```

- 단점
    - 정의된 모듈의 위치를 알기 어려워 명시적이지 않을 수 있음
    - 사용자가 선언한 변수 또는 함수와 겹치게 되어 모듈에서 정의한 값이나 동작이 이루어지지 않을 수 있음
        
        ```python
        # from 절 단점
        from math import sqrt
        
        math_result = sqrt(16)  # 실수형 4.0
        
        def sqrt(x):  # 사용자가 정의한 sqrt 함수
            return str(x**0.5)
        
        my_result = sqrt(16)  # 문자열 4.0
        
        print(type(math_result), type(my_result))  # <class 'float'> <class 'str'>
        ```
        

### from 절 사용 시 주의사항

- 서로 다른 모듈에서 import 된 변수나 함수의 이름이 같은 경우 이름 충돌 발생
    - 마지막에 import된 것이 이전 것을 덮어쓰기 때문에, 나중에 import된 것만 유효함
        
        ```python
        # from 절 사용 주의 사항
        ## 같은 이름인 경우 덮어쓰기 주의
        from math import sqrt  # math.sqrt가 먼저 import됨
        from my_math import sqrt  # my_math.sqrt가 math.sqrt를 덮어씀
        
        result = sqrt(9)  # math.sqrt가 아닌 my_math.sqrt가 사용됨
        
        ```
        
    - 모든 요소를 한꺼번에 import하는 `*` 표기는 권장하지 않음
        
        ```python
        # from 절 사용 주의 사항
        ## 모든 요소를 한 번에 import 하는 * 은 권장하지 않음
        from math import *
        from my_math import sqrt, tangent  # 어느 함수가 math 모듈과 중복되는지 모름
        
        # 아래는 사용자가 임의로 정의한 변수들
        a = 100
        c = 200
        e = 300  # math 모듈의 자연상수 e를 사용할 수 없게 됨
        ```
        
        → 따라서 모듈명을 쓸 수 있는 표기법이 권장됨.
        
        - 너무 깊은 모듈일 경우 내가 원하는 함수까지 도달하기에 너무 많은 단계를 거침 → 이 경우 from import 사용
        - 이외의 경우 import 사용

### `as` 키워드

- `as` 키워드를 사용하여 별칭(alias)을 부여
    - 두 개 이상의 모듈에서 동일한 이름의 변수, 함수 클래스 등을 가져올 때 발생하는 이름 충돌 해결
    
    ```python
    ## as 키워드 사용 1
    from math import sqrt
    from my_math import sqrt as my_sqrt
    
    print(sqrt(4))  # 2.0
    print(my_sqrt(4))  # 2.0
    ```
    
- import 되는 함수나 변수명이 너무 길거나 자주 사용해야 할 경우 `as` 키워드로 별칭을 정의해 쉽게 사용
    
    ```python
    ## as 키워드 사용 2
    ## (참고) pandas와 matplotlib 패키지 설치해야 정상 동작
    import pandas
    import matplotlib.pyplot
    
    # 별칭을 부여하지 않으면 길고 불편함
    df = pandas.DataFrame()
    matplotlib.pyplot.plot(x, y)
    
    import pandas as pd
    import matplotlib.pyplot as plt
    # 별칭을 사용하면 짧고 편리
    df = pd.DataFrame()
    plt.plot(x, y)
    ```

### 내장함수 help를 사용해 모듈에 무엇이 들어있는지 확인 가능

`help(module_name)`