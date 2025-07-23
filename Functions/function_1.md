# 함수

## 함수의 정의

### 함수(Function)

- 특정 작업을 수행하기 위한 **재사용 가능한 코드 묶음**

### 함수를 사용하는 이유

- 두 수의 합을 구하는 함수를 정의하고 사용함으로써 코드의 중복을 방지
- 재사용성이 높아지고, 코드의 **가독성**과 **유지보수성** 향상

```python
# 두 수의 합을 구하는 코드
num1 = 5
num2 = 3
sum_result = num1 + num2

print(sum_result)

# 두 수의 합을 구하는 함수
## 함수 정의
num1 = 5
num2 = 3
def get_sum(num1 + num2) :
	return num1 + num2
	
## 함수 call
get_sum(num1, num2)
```

### 함수 호출(function call)

- 함수를 실행하기 위해 함수의 이름을 사용하여 해당 함수의 코드블록을 실행하는 것
- 표기법: `fucn_name(args)`
    
    ```python
    # 두 수의 합을 구하는 함수
    ## 함수 정의
    num1 = 5
    num2 = 3
    def get_sum(num1 + num2) :
    	return num1 + num2
    	
    ## 함수 call
    get_sum(num1, num2)
    ```
    

## 함수 구조

### 함수구조 1)

- input: `parameters` 
→ [ Docstirng(설명서-optional): `"""` / function body: 무언가 연산이 이루어짐: 들여쓰기 ] 
→ output: `return value`

### 함수 정의와 호출

- 함수 정의 `def func_name(param1, param2)`
    - 함수 정의는 `def` 키워드로 시작
    - `def` 키워드 이후 함수 이름 작성
    - 괄호 안에 매개변수 정의 가능
    - 매개변수(parameter)는 함수에 전달되는 값
- Docstring
    - 함수 body 앞에 선택적으로 작성 가능한 함수 설명서
    - `"""` 주석 사용
- 함수 body
    - 콜론(`:`) 다음에 들여쓰기 된 코드 블록
    - 함수가 실행될 때 수행되는 코드를 정의
- 함수 반환 값 `return`
    - 함수는 필요한 경우 결과를 반환할 수 있음
    - `return` 키워드 이후에 반환할 값을 명시
    - `return` 문은 함수의 실행을 종료하고 결과를 호출 부분으로 반환
    - 함수 내에서 `return` 문이 없다면 `None`이 반환됨
- 함수 호출
    - 함ㅅ를 사용하기 위해서는 호출이 필요
    - 함수의 이름과 소괄호를 활용해 호출
    - 필욯나 경우 인자를 전달해야 함
    - 호출 부분에서 전달된 인자는 함수 정의 시 작성한 매개변수에 대입

### 이론 - print() 함수는 반환값이 없음

- `print()` 함수는 화면에 값을 출력하기만 할 뿐, 반환(`return`) 값이 없음
- 파이썬에서 반환값이 없는 함수는 기본적으로 None을 반환한다고 간주되기 때문

### 이론 - 매개변수와 인자

- 매개변수(parameter)
    - 함수를 정의할 때, 함수가 받을 값을 나타내는 변수
    - 인자(argument)
        - 함수를 호출할 때 실제로 전달되는 값

```python
def add_numbers(x, y):  # x와 y는 매개변수
    result = x + y
    return result

a = 2
b = 3

sum_result = add_numbers(a, b)  # a와 b는 인자
print(sum_result)  # 5

```

### 이론 - 다양한 인자 종류

1. Positional Argumets (위치인자)
    1. 함수 호출 시 인자의 위치에따라 전달되는 인자
    2. 위치 인자는 함수 호출 시 반드시 값을 전달해야 함
    
    ```python
    # 1. Positional Arguments
    def greet(name, age):
        print(f'안녕하세요, {name}님! {age}살이시군요.')
    
    greet('Alice', 25)  # 안녕하세요, Alice님! 25살이시군요.
    greet(25, 'Alice')  # 안녕하세요, 25님! Alice살이시군요.
    greet('Alice')  # TypeError: greet() missing 1 required positional argument: 'age'
    
    ```
    
2. Default Argument Values(기본 인자 값)
    1. 함수 정의에서 매개변수에 기본 값을 할당하는 것
    2. 함수 호출 시 인자를 전달하지 않으면, 기본값이 매개변수에 할당됨
    3. 매개변수에 지정된 데이터 타입은 중요하지 않음. 
    → 함수를 호출 할 때 인자의 데이터 타입으로 지정됨. 
    
    ```python
    # 2. Default Argument Values
    def greet(name, age=20):
        print(f'안녕하세요, {name}님! {age}살이시군요.')
    
    greet('Bob')  # 안녕하세요, Bob님! 30살이시군요.
    greet('Charlie', 40)  # 안녕하세요, Charlie님! 40살이시군요.
    ```
    
3. Keyword Arguments(키워드 인자)
    1. 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자
    2. 매개변수와 인자를 일치시키지 않고, 특정 매개변수에 값을 할당할 수 있음
    3. 인자의 순서는 중요하지 않으며, 인자의 이름을 명시하여 전달
    4. **단, 호출 시 키워드 인자는 위치 인자 뒤에 위치해야 함**
    
    ```python
    # 3. Keyword Arguments
    def greet(name, age):
        print(f'안녕하세요, {name}님! {age}살이시군요.')
    
    greet(name='Dave', age=35)  # 안녕하세요, Dave님! 35살이시군요.
    greet(age=35, name='Dave')  # 안녕하세요, Dave님! 35살이시군요.
    greet(age=35, 'Dave')  # Positional argument cannot appear after keyword arguments
    ```
    
4. **Arbitrary Argument Lists(임의의 인자 목록) - 가변**
    1. **정해지지 않은 개수의 인자**를 처리하는 인자
    2. 함수 정의 시 매개변수 앞에 `*`를 붙여서 사용
    3. 여러 개의 인자를 tuple로 처리
        1. **순서가 필요할 때 ! list로 형변환이 필요할 때 !**
5. **Arbitrary Keyword Argument Lists(임의의 키워드 인자 목록) - 가변 키워드**
    1. 정해지지 않은 개수의 키워드 인자를 처리하는 인자
    2. 함수 정의 시 매개변수 앞에 `**` 를 붙여서 사용
    3. 여러 개의 인자를 **dictionary**로 묶어 처리
    
    ```python
    # 5. Arbitrary Keyword Argument Lists
    def print_info(**kwargs):
        print(kwargs)
    
    print_info(name='Eve', age=30)  # {'name': 'Eve', 'age': 30 }
    
    ```
    
- 함수 인자 권장 작성 순서
    - 위치 → 기본 → 가변 → 가변 키워드
        - 위치인자는 구조상 뒤로 갈 수가 없어 앞에서 정의가 끝나야 함.
        - python의 입장에서 이해해보기
    - 호출 시 인자를 전달하는 과정에서 혼란을 줄일 수 있도록 함
    - 단, 모든 상황에 적용되는 절대적인 규칙은 아니며, 상황에 따라 유연하게 조정될 수 있음
    
    ```python
    # 인자의 모든 종류를 적용한 예시
    def func(pos1, pos2, default_arg='default', *args, **kwargs):
        print('pos1:', pos1)
        print('pos2:', pos2)
        print('default_arg:', default_arg)
        print('args:', args)
        print('kwargs:', kwargs)
    
    func(1, 2, 3, 4, 5, 6, key1='value1', key2='value2')
    """
    pos1: 1
    pos2: 2
    default_arg: 3
    args: (4, 5, 6)
    kwargs: {'key1': 'value1', 'key2': 'value2'}
    """
    ```
    
    - 매개변수의 타입을 강제할 수 있는가?
        - Type Hints를 사용해 타입을 권장할 수는 있으나 강제할 수는 없다.
        - 경고 메시지를 띄우지만 실행 자체는 정상적으로 가능
        
        ```python
        # 1. 기본 - 변수명: 자료형 = 값
        a: str = "abcde"
        b: float = 2.5
        c: list = [1, 3, 5]
        
        a = 400
        
        # 2. 변수 선언 시 Typing 모듈을 활용하여 내부 값 자료형 명시
        from typing import List, Dict
        
        c: List[int] = [1, 3, 5]
        
        d: Dict[int, str] = {1: 'a', 2: 'b'}
        
        # 3. 함수 선언 시 input, output 타입 명시 
        def add(a: int, b: int) -> int:
            return a + b
            
        # 4. 일부 변수만 설정도 가능
        from typing import List
        ## 4.1. input의 일부 변수만 타입을 명시한 경우
        def mul(a: float, b):
            return a * b
        
        ## 4.2. typing 모듈의 기능을 활용하여 입력/출력 값들의 타입을 명시한 경우
        def add_list(a: List[int], b: List[int]) -> List[int]:
            if len(a) != len(b):
                return [-1]
        
            result = []
            for i in range(len(a)):
                result.append(a[i] + b[i])
            return result
        ```
        

# 함수 스타일 가이드

## 함수 이름 작성 규칙

### 기본 규칙

- 소문자와 언더스코어(*) 사용 → `snake_*case`
- 동사로 시작하여 함수의 동작 설명
- 약어 사용 지양

```python
# Good
def calculate_total_price(price, tax):
    return price + (price * tax)

# Bad
def calc_price(p, t):
    return p + (p * t)
```

### 함수 이름 구성 요소

- 동사 + 명사
    - `save_user()`
- 동사 + 형용사 + 명사
    - `calculate_total_price()`
- get/set 접두사
    - `get_username()` : 값을 추출, `set_username()` : 값을 만듦
- **TIP**
    - 이름 만으로 ‘무엇을 하는지’ 명확하게 표현
    - **True/False**를 반환한다면 **is** 또는 **has**로 시작하는 걸 추천
    - 프로젝트 전체에서 **일관성**을 지키는 것이 **가독성**에 도움을 줌

## 단일 책임 원칙

### 단일 책임 원칙(Single Responsibility Principle)

- 모든 객체는 하나의 명확한 목적과 책임만을 가져야 함

### 함수 설계 원칙

1. **명확한 목적**
    - 함수는 한 가지 작업만 수행
    - 함수 이름으로 목적을 명확히 표현
2. **책임 분리**
    - 데이터 검증, 처리, 저장 등을 별도 함수로 분리
    - 각 함수는 독립적으로 동작 가능하도록 설계
3. **유지보수성**
    - 작은 단위의 함수로 나누어 관리
    - 코드 수정 시 영향 범위를 최소화
    
    ```python
    # 올바른 설계 예시 (책임을 분리한함수들)
    def validate_password(password):
        """비밀번호 유효성 검사"""
        if len(password) < 8:
            raise ValueError('비밀번호는 8자 이상이어야 합니다')
    
    def save_user(user_data):
        """비밀번호 암호화 및 저장"""
        user_data['password'] = hash_password(user_data['password'])
        db.users.insert(user_data)
    
    def send_welcome_email(email):
        """환영 이메일 발송"""
        send_email(email, '가입을 환영합니다!')
    
    # 메인 함수에서 순차적으로 실행
    def process_user_data(user_data):
        validate_password(user_data['password'])
        save_user(user_data)
        send_welcome_email(user_data['email'])
    
    ```
    

## 함수와 반환

### 함수의 return, 반환의 원칙

- 파이썬 함수는 언제나 단 하나의 값(객체)만 반환할 수 있음
- 여러 값을 반환하는 경우에도 하나의 튜플로 패킹하여 반환

```python
def get_user_info():
    name = 'Alice'
    age = 30
    # 콤마(,)로 여러 값을 반환하는 것처럼 보임
    return name, age

# 하지만 반환된 값을 user_data변수에 담아 확인해보면
user_data = get_user_info()

# 단 하나의 튜플을 반환하는 것 입니다.
print(user_data)  # ('Alice', 30)
```