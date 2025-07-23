## Range

- 연속된 정수 시퀀스를 생성하는 **변경 불가능(immutable)**한 자료형
- **주로 반복문**과 함께 사용되어 **특정 횟수만큼** 코드를 반복 실행할 때 매우 유용
- 실제로 모든 숫자를 **메모리에 저장하는 대신** 시작 값, 끝 값, 간격이라는 ‘규칙’만 기억하여 메모리를 **매우 효율적으로 사용**
- range의 기본 구문
    - range()는 1개, 2개, 또는 3개의 **매개변수**(**인자**)를 가질 수 있음
        - 매개변수: 함수를 정의할 때, 함수가 받을 값을 나타내는 변수
        - 인자: 함수를 호출할 때 실제로 전달되는 값
        - `range(start, stop, step)`
            - `range(stop)` : `range(n)` 에서 `0` ~ `n-1` 까지
            
            ```python
            print(my_range_1)  # range(0, 5)
            print(list(my_range_1))  # [0, 1, 2, 3, 4]
            ```
            
            - `range(start, stop)` : `range(n,m)` : `n` ~ `m-1` 까지
            - `range(statr, stop, step)` : `range(x,y,z)` : `x` , `x+z` , `x+2*z` … `y-z`
    - range의 규칙
        - 값의 범위 규칙
            - stop 값은 생성되는 시퀀스에 절대 포함되지 않음
            - range(1,5)는 1부터 5 ‘전’까지의 숫자를 의미하므로, 1, 2, 3, 4가 생성
        - 증가/감소 값(step) 규칙
            - step 값은 숫자 시퀀스의 간격과 방향을 결정
                1. step이 양수일 때 (기본값:1)
                    - 숫자가 start부터 stop을 향해 증가
                    - range(1, 10, 2) → 1, 3, 5, 7, 9
                    
                    ```python
                    # 시작 값이 끝 값보다 작은 경우 (정상)
                    print(list(range(1, 5)))  # [1, 2, 3, 4]
                    # 시작 값이 끝 값보다 큰 경우
                    print(list(range(5, 1)))  # []
                    ```
                    
                2. step이 음수일 때 
                    - 숫자가 start 부터 step을 향해 감소
                    - 이 경우 start 값은 stop보다 반드시 커야 함
                    - range(10, 1, -2) → 10, 8, 6, 4, 2
                    
                    ```python
                    # 시작 값이 끝 값보다 큰 경우 (정상)
                    print(list(range(5, 1, -1)))  # [5, 4, 3, 2]
                    # 시작 값이 끝 값보다 작은 경우
                    print(list(range(1, 5, -1)))  # []
                    
                    ```
                    
    - range 활용 예시