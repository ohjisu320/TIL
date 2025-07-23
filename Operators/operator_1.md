# 연산자

<aside>
💡

## 산술연산자

- 수학적 계산을 위해 사용되는 연산자
    
    
    | 기호 | 설명 |
    | --- | --- |
    | `+` | 덧셈 |
    | `-` | 뺄셈 |
    | `*` | 곱셈 |
    | `/` | 나눗셈 |
    | `//` | 몫 나눗셈 |
    | `%` | 나머지 |
    | `**`  | 거듭제곱 |
    | `-` | 음수 부호 |
</aside>

<aside>
💡

## 복합 연산자

- 연산과 할당이 함께 이뤄짐
    
    
    | 기호 | 예시 | 의미 |
    | --- | --- | --- |
    | `+=` | a += b |  a = a + b |
    | `-=` | a -= b |  a = a - b |
    | `*=` | a *= b |  a = a * b |
    | `/=` | a /= b |  a = a / b |
    | `//=` | a //= b |  a = a // b |
    | `%=` | a %= b |  a = a % b |
    | `**=` | a **= b |  a = a ** b |
- 가독성 = 명시도가 중요하기에 산술연산자가 때론 더 좋을 수도 있음
</aside>

<aside>
💡

## 비교 연산자

- 두 값을 비교하여 그 관계가 맞는지 틀리는지를   True 와 False로 변환
    
    
    | 기호 | 내용 |
    | --- | --- |
    | `<` | 미만 |
    | `<=` | 이하 |
    | `>` | 초과 |
    | `>=` | 이상 |
    | `==` | 같음 |
    | `!=` | 같지 않음 |
    | `is` | 같음 |
    | `is not` | 같지 않음 |
</aside>

- == 연산자
    - 값(데이터)이 같은지를 비교
    - 동등성(equality)
    - 예를 들어 1 == True의 경우 파이썬이 내부적으로 True 를 1로 간주할 수 있으므로 True 결과가 나옴
        
        ```python
        # == 연산자
        print(2 == 2.0)  # True - 암시적 형변환을 받아들임
        print(2 != 2)  # False
        print('HI' == 'hi')  # False
        print(1 == True)  # True - 암시적 형변환을 받아들임
        ```
        
- is 연산자
    - 객체 자체가 같은지를 비교
    - 식별성(identity})
    - 두 변수가 완전히 동일한 객체를 가리키는지, 즉 메모리 주소가 같은지를 확인할 때 사용
    - 특수한 케이스를 제외하고는 equality를 씀
    
    ```python
    # is 연산자
    # SyntaxWarning: "is" with a literal(표현법). Did you mean "=="?
    # is는 메모리 주소를 비교하는 데, 값 자체를 비교하는 ==를 써야 할 곳에 실수로 사용한 것 같다고 파이썬이 알려주는 경고
    
    # 아래 두 코드는 오류가 뜨지는 않지만 warning message가 뜨게 됨.
    print(1 is True)  # False
    print(2 is 2.0)  # False
    ```
    
    - is 대신 ==를 사용해야 하는 이유
        - 결론: is는 ‘정체성’을, ==는 ‘가치’를 비교하기 때문
    - is를 값비교에 사용하면 안되는 이유 - 의도와 다른 결과를 낳음
        - 아래 코드에서는  is는 “두 객체가 메모리 상에서 같은 존재인가?”를 묻기 때문에 False가 출력됨
    - is 연산자는 언제 사용하는가?
        - 주로 싱글턴 객체를 비교할 때 사용함
            - 싱글턴 객체란?
                - 특정 값에 대해 파이썬 전체에서 단 하나의 객체만 생성되어 재사용되는 특별한 객체
                - 여러 변수가 이 값을 가지더라도 다 같은 메모리 주소를 가리키기 때문에 다 같은 객체로 인식함
                - None, True, False
                - 싱글턴 객체를 비교할 때
                
                ```python
                # is 연산자는 언제 사용하는가?
                # 싱글턴 객체 비교할 때
                # 다만 에러나 경고문을 띄우지 않음ㄴ
                x = None
                # 권장
                if x is None:
                    print('x는 None입니다.')
                # 비권장
                if x == None:
                    print('x는 None입니다.')
                
                x = True
                y = True
                print(x is y)  # True
                print(True is True)  # True
                print(False is False)  # True
                print(None is None)  # True
                ```
                
- 리스트나 객체 비교 시 주의사항
    - 리스트 또는 다른 가변 객체를 비교할 때 값 자체가 같은 지 확인하려면 ==를 사용
    - 두 변수가 완전히 동일한 객체를 가리키는지를 확인해야 한다면 is를 사용
        
        ```python
        # a와 b에 같은 '값'을 할당할 경우
        a = [1, 2, 3]
        b = [1, 2, 3]
        print(a == b) # True (두 리스트의 값은 동일)
        print(a is b) # False (서로 다른 리스트 객체)
        
        # b가 a를 그대로 참조하도록 할 경우
        b = a
        print(a is b) # True (같은 객체를 가리키므로 True)
        ```
        
- ==와 is 정리
    - 값 비교에는 == 사용, None/True/False 비교할 때는 is 사용

<aside>
💡

## 논리 연산자

- 여러 개의 조건을 조합하거나, True/False 값을 반대로 뒤집을 때 사용 (and, or, not이 대표적)
    
    
    | 기호 | 연산자 | 내용 |
    | --- | --- | --- |
    | `and` | 논리곱 | 두 피연산자 모두 True인 경우에만 전체 표현식을 True로 평가 |
    | `or` | 논리합 | 두 피연산자 중 하나라도 True인 경우 전체 표현식을 True로 평가 |
    | `not` | 논리부정 | 단일 피연산자를 부정 |
</aside>

- 논리연산자 활용
    
    ```python
    # 논리 연산자
    print(True and False)  # False
    print(True or False)  # True
    print(not True)  # False
    print(not 0)  # True
    ```
    
- 비교연산자와 함께 사용 가능
    
    ```python
    # 논리 연산자 & 비교 연산자
    num = 15
    result = (num > 10) and (num % 2 == 0)
    print(result)  # False
    
    name = 'Alice'
    age = 25
    # python은 첫 구문에서 True 평가가 나왔다면 뒷 구문은 평가하지 않음 == 단축평가
    result = (name == 'Alice') or (age == 30)
    print(result)  # True
    
    ```
    
- 단축평가
    - 논리 연산에서 두 번째 피연산자를 평가하지 않고 결과를 결정하는 동작
    - 컴퓨터는 생각보다 ‘게으른’구석이 있음
    - 꼭 필요한 계산만 하고 결과가 이미 정해졌다면 굳이 뒤에 있는 코드까지 확인하지 않음
    - 이렇게 결과가 확정되는 순가 평가를 ‘단축’하고 넘어간다고 해서 ‘단축 평가’라고 부름
    
    - 파이썬의 참과 거짓에 대한 새로운 시각
        - 거짓으로 취급되는 값들
            - False, 숫자 0, 빈 문자열 “”, 빈 리스트 [], None 등
        - 참으로 취급되는 값들
            - True 그리고 ‘거짓’이 아닌 모든 값
            - 1, —10, “hello”, [1, 2]  등 내용이 있는 값
    
    ```python
    # 1
    # 준비물 1: 내용이 있는 문자열
    item1 = '지도'
    # 준비물 2: 내용이 있는 문자열
    item2 = '나침반'
    result = item1 and item2 # item2 까지 평가 -> True
    print(f'최종적으로 챙긴 물건: {result}')
    # >> 최종적으로 챙긴 물건: 나침반
    
    # 2
    item1 = '지도'
    # 준비물 2: 내용이 없는 빈 문자열
    item2 = '' # False
    result = item1 and item2 # item2 까지 평가 -> False
    print(f'최종적으로 챙긴 물건: "{result}"')
    # >> 최종적으로 챙긴 물건: ''
    
    # 3
    # 준비물 1: 내용이 없는 빈 문자열
    item1 = '' # False
    item2 = '나침반'
    result = item1 and item2 # item1까지만 평가 -> False
    print(f'최종적으로 챙긴 물건: "{result}"')
    # >> 최종적으로 챙긴 물건: ''
    
    ```
    
    - 단축평가를 하는 이유
        - 코드 실행을 최적화하고 불필요한 연산을 피할 수 있도록 함
        - 단순히 True/False 논리 연산을 넘어, 이처럼 코드의 흐름을 제어하고, 오류를 방지하며 간결한 코들르 생성하는 데 매우 유용하게 사용되는 파이썬의 중요한 기능

<aside>
💡

## 멤버십 연산자

- 특정 값이 시퀀스나 다른 컬렉션 안에 포함되어 있는지 확인하는 연산자 
e.g. `if '홍길동' in emp_list`

| 기호 | 내용 |
| --- | --- |
| in | 왼쪽 피연산자가 오른쪽 피연산자의 시퀀스에 속하는지를 확인 |
| not in | 왼쪽 피연산자가 오른쪽 피연산자의 시퀀스에 속하지 않는지를 확인 |
</aside>

```python
# 멤버십 연산자

word = 'hello'
numbers = [1, 2, 3, 4, 5]

print('h' in word)  # True
print('z' in word)  # False

print(4 not in numbers)  # False
print(6 not in numbers)  # True

```

<aside>
💡

## 시퀀스형 연산자

- 시퀀스 자료형(문자열, 리스트, 튜플)에 특별한 의미로 사용되는 연산자
- ‘+’는 시퀀스를 연결하는 기능을, ‘*’는 시퀀스를 반복하는 기능을 함

| 연산자 | 내용 |
| --- | --- |
| + | 결합 연산자 |
| * | 반복 연산자 |

```python
# 시퀀스형 연산자

print('Gildong' + ' Hong')  # Gildong Hong
print('hi' * 5)  # hihihihihi

print([1, 2] + ['a', 'b'])  # [1, 2, 'a', 'b']
print([1, 2] * 2)  # [1, 2, 1, 2]

```

</aside>

# 연산자 우선순위

**산술**연산자 > **비교**연산자 > **객체** 비교 is / is not > **멤버십** 연산자 > **논리**연산자

산술연산자에 익숙하니깨 … 산술연산자 먼저 수행

논리연산자 중에서는 not > and > or

![image.png](attachment:6bdba7f9-f687-4a78-9220-be1f12882884:image.png)

# 참고

## Trailing Comma

- 컬렉션의 마지막 요소 뒤에 붙는 쉼표
- 일반적으로 Trailing Comma 작성은 ‘선택사항’
- 단 하나의 요소로 구성된 튜플을 만들 때는 필수

- Trailing Comma 좋은 예시
    
    ```python
    # Good
    
    item = [
    		'item1',
    		'item2',
    ]
    
    my_func(
    		'value1',
    		'value2',
    )
    ```
    
- Trailing Comma 나쁜 예시
    
    ```python
    # Bad
    
    items = ['item1', 'item2',]
    my_func('value1', 'value2',)
    
    # 한 줄 작성 시에는 불필요
    items = ['item1', 'item2']
    my_func('value1', 'value2')
    ```
    

# 궁금한 점

1. 다음 코드의 결과로 올바른 것을 고르시오.

```python
x = 0
print(x or 5)

# a) 0
# b) 5
# c) True
# d) None
```

- 먼저 `A`를 평가해서 **참(True)** 이면 그 값을 바로 반환
그렇지 않으면(B도 평가하지 않고) **`B`** 를 반환합니다.
- **`x = 0`일 때의 평가**
    - 숫자 `0`은 Python에서 `False`로 취급되는 **거짓(false)** 값입니다.
    - 따라서 `x or 5`에서 `x`(즉 `0`)은 거짓이므로, `or`는 다음 피연산자인 `5`를 반환합니다.
- **`or`는 첫 번째 피연산자의 진릿값(truth value)을 검사**
    - 첫 번째 피연산자가 **참(True)** 이면,  **첫 번째 피연산자 자체**를 반환
    - 첫 번째 피연산자가 **거짓(False)** 이면, 두 번째 피연산자를 평가하고 그 **두 번째 피연산자 자체**를 반환
- **“거짓(False)”인 값들 예시**
    - `0`, `0.0`, `""` (빈 문자열), `[]` (빈 리스트), `None`, `False` 등은 모두 거짓으로 취급됩니다.
- `x = 0` 일 때
    
    ```python
    x or 5
    # x가 0 → falsy
    # 그래서 or는 x를 버리고, 5(두 번째 피연산자)를 그대로 반환
    ```
    
- **왜 Boolean이 아닌 원래 값을 반환할까?**
    - Python 설계상 `and`·`or`는 “단순 논리 연산” 기능뿐 아니라 “짧은 회로 평가(short‑circuit evaluation)”를 활용해 **첫 번째로 확정된 값을 곧장 돌려줍니다**.
    - 예를 들어 `a and b` 에서
        
        `and`는 “둘 다 참이어야 전체가 참”이기 때문에,
        
        - 첫 번째 피연산자 `a`가 거짓(False)이면 결과가 거짓임이 확정
        → 두 번째 `b`는 평가조차 **하지 않고** 바로 `a`를 반환
            - `a`가 False → 즉시 `a` 반환
            - `a`가 True → `b` 반환
    - 이러한 특징 덕분에,
        
        ```python
        result = config_value or default_value
        ```
        
        처럼 “만약 `config_value`가 설정돼 있지 않으면 `default_value`를 쓰라”는 패턴을 간편히 사용할 수 있습니다.