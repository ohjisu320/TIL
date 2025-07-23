# Other Types

<aside>
💡

## None

- 파이썬에서 값이 없음을 표현하는 특별한 데이터 타입
- 마치 내용물이 없는 ‘빈 상자’와 같음
- 숫자 0이나 빈 문자열( ‘’ )과는 다른, **값이 존재하지 않음** 또는 **아직 정해지지 않음**이라는 상태를 나타태기 위해 사용됩니다. **- 시험 나올듯**
    - `a = 0`  ≠ `b = ''`  ≠ `c = None`
</aside>

- None 표현
    - 아직 아무 값도 할당하고 싶지 않을 때
        
        ```python
        my_variable = None
        print(my_variable)  # None
        ```
        
        함수에 return 값을 실수로 누락하거나 지정하지 않았다면 기본적으로 None을 반환하게 됨
        

<aside>
💡

## Boolean (True / False)

- 참과 거짓 단 두 가지 값만 가지는 데이터 타입
</aside>

- 비교 / 논리 연산의 평가 결과로 사용됨
    
    ```python
    # Boolean
    is_active = True
    is_logged_in = False
    
    print(is_active)  # True
    print(is_logged_in)  # False
    print(10 > 5)  # True
    print(10 == 5)  # False
    ```