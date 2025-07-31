# 프로그래밍 패러다임

## 절차 지향과 객체 지향

### 절차 지향 프로그래밍 (Procedural Programming)

- 함수와 로직 중심 작성
- 데이터를 **순차적으로 처리**
    
    ⇒ 순서대로 작업을 지시하는 방식
    
    ⇒ 모든 과정이 위에서 아래로 차례차례 실행되도록 구성
    

### 절차 지향 사고 예시

- 변수와 함수를 별개로 다룸

```python
# 예: 변수와 함수를 별개로 다룸
# 데이터
name = 'Alice'
age = 25

# 함수
def introduce(name, age):
    print(f'안녕하세요, {name}입니다. 나이는 {age}살입니다.')

# 결과
introduce(name, age)
```

### 절차 지향 프로그래밍 특징

- 입력을 받고, 처리하고, 결과를 내는 과정이 위에서 아래로 순차적으로 흐르는 형태
- 순차적인 명령어 실행
- 데이터와 함수(절차)의 분리
- 함수 호출의 흐름이 중요

⇒ 데이터를 다시 재사용하기 보다는 처음부터 끝까지 실행되는 결과물이 중요

### 절차 지향적 프로그래밍의 한계

1. 복잡성 증가
    - 프로그램 규모가 커질수록 데이터와 함수의 관리가 어려움
    - 전역 변수의 증가로 관리의 어려움
2. 유지보수 문제
    - 코드 수정 시영향 범위 파악이 어려움

### 객체 지향 프로그래밍(Object Oriented Programming)

- 클래스는 **설계도**, 인스턴스는 **실제 물건**
- 자동차를 만들기 위한 설계도는 **클래스**, 이 설계도를 바탕으로 실제로 조립된 자동차 한 대 한 대가 **인스턴스**
- 같은 클래스를 써도 인스턴스는 서로 다른 속성을 가질 수 있음 → 인스턴스는 서로 독립
- Python에서도 그 클래스를 바탕으로 여러 개의 인스턴스를 만들 수 있음
- 클래스에는 속성과 메서드가 설립되어 있음
- 클래스 : Blueprint-청사진

### 객체 지향 사고 예시

- 사람(객체) 안에 name, age와 이와 관련된 기능(메서드) 포함

```python

# 객체 지향 사고
# 예: 사람(객체) 안에 name, age와 이와 관련된 기능(메서드) 포함
class Person:
    def __init__(self, name, age): 
        self.name = name
        self.age = age

    def introduce(self): # Person이라는 class의 method
        print(f'안녕하세요, {self.name}입니다. 나이는 {self.age}살입니다.')

alice = Person('Alice', 25) # alice == Person이 찍어낸 인스턴스
alice.introduce()  # 객체가 자신의 정보를 출력

```

### 객체 지향 프로그래밍 특징

- 프로그램을 데이터(변수)와 그 데이터를 처리하는 함수(메서드)를 하나의 단위(객체)로 묶어서 조직적으로 관리
- 데이터(야채, 칼)와 메서드(볶기, 썰기)의 결합 ⇒ 볶음밥 기계

### 절차지향 & 객체지향

- 절차지향
    - 데이터와 해당 데이터를 처리하는 함수(절차)가 분리
    - 함수 호출의 흐름이 중요
    - 어떤 순서로 처리할까??
- 객체 지향
    - 데이터와 해당 데이터를 처리하는 메서드를 하나의 객체로 묶음
    - 객체 간 상호작용과 메시지 전달이 중요
    - 어떤 객체가 이 문제를 해결할까??
    - 이 객체는 어떤 속성과 기능을 가질까??

### 객체지향 - 데이터가 살아나다

- 객체 지향은 수동적인 데이터가 능동적인 객체로 변화한 것
- 절차 지향에서는 데이터가  함수의 매개변수로 전달되어 처리되는 수동적 존재였지만, 객체 지향에서는 데이터와 해당 데이터를 처리하는 메서드가 하나의 객체로 통합되어 스스로 기능을 수행하는 능동적 존재가 됨
- 이는 코드의 구조화와 재사용성을 높이는 동시에,
실제 세계의 모델링 방식과 더 유사한 프로그래밍을 가능하게 함

### 주의 사항

- 절차 지향과 객체 지향은 대조되는 개념이 아님
    - 객체 지향은 기존 절차 지향을 기반으로 두고 보완하기 위해 객체라는 개념을 도입해
    상속, 코드 재사용성, 유지보수성 등의 이점을 가지는 패러다임

## 객체와 클래스

### 객체(Object)

- 실제 존재하는 사물을 추상화한 것
- “속성”과 “동작”을 가짐
- 예를 들어 강아지라는 객체는 이름, 종, 나이(특징)와 짖기, 뛰기(행동) 등으로 표현할 수 있음

### 클래스(Class)

- 객체를 만들기 위한 설계도
- 테이터와 기능을 함께 묶는 방법을 제공
- 파이썬에서 타입을 표현하는 방법

- 클래스로부터 여러 개의 객체를 쉽게 만들어낼 수 있음

### 객체 예시

- 가수라는 객체를 찍어내는 **Class**
    - 속성(정보) → **변수**
        - 직업 - 가수
        - 생년월일 - 1993 0…
        - 국적 - 대한민국
    - 동작(행동) → **메서드**
        - 랩()
        - 댄스()
        - 바이브레이션()

### 객체 특징

- 속성
    - 객체의 상태 / 데이터
- 메서드
    - 객체의 행동 / 기능
- 고유성
    - 각 객체는 고유한 특성을 가져서 서로 영향을 미치지 않음

# 클래스 기초

## 클래스

### 클래스(Class)

- 클래스는 하나의 구조 안에 데이터(변수)와 기능(함수)을 함께 정의하는 도구
- 서류 작성할 때, 양식은 클래스 / 채워진 서류는 인스턴스
- 여러 인스턴스를 일관되게 만들어내는 틀 역할

### 클래스 정의

- class 키워드
- 클래스 이름은 파스칼 케이스(Pascal Case) 방식으로 작성
    - 왜? 클래스인 걸 이름만 보고도 구분할 수 있도록
    - snake_case로 이름을 만들 수는 있지만 절대 X
    
    ```python
    class MyClass :
    		pass
    ```
    

### 클래스 예시

- `__init__`  메서드는 생성자 메서드로 불리며
새로운 객체를 만들 때 필요한 초기값을 설정 (메서드 챕터에서 진행)
    - initialize의 약자 - 초기화
    - `__<method>__` 은 매직메서드
    
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name  # 인스턴스 속성
            self.age = age  # 인스턴스 속성
    
        def introduce(self):
            print(f'안녕하세요. 저는 {self.name}, 나이는 {self.age}살입니다.')
    
    ```
    

## 인스턴스

### 인스턴스(instance)

- 클래스를 통해 생성된 객체
- 인스턴스는 클래스를 사용해 실제로 만들어진 객체
- 같은 클래스로 여러 인스턴스를 만들 수 있으며,
각 인스턴스는 클래스 구조를 따라 동작하지만 서로 독립된 데이터를 가질 수 있음

### 인스턴스 예시

- 클래스가 설계도라면, 인스턴스는 그 설계도로부터 실제로 만들어진 ‘개별 물건’
    
    ```python
    class Person:
        def __init__(self, name, age):
            self.name = name  # 인스턴스 속성
            self.age = age  # 인스턴스 속성
    
        def introduce(self):
            print(f'안녕하세요. 저는 {self.name}, 나이는 {self.age}살입니다.')
    
    # 인스턴스 생성
    p1 = Person("Alice", 25)
    p2 = Person("Bella", 25)
    
    # 인스턴스 내부 메서드 호출
    p1.introduce()
    p2.introduce()
    
    # 변수 확인
    print(p1.name)
    print(p2.name)
    
    # p1 = Person().introduce("Alice", 25) # TypeError: Person.__init__() missing 2 required positional arguments: 'name' and 'age'
    
    ```
    

## 클래스와 인스턴스

### 클래스와 인스턴스

- 클래스를 정의한다는 것은 공통된 특성과 기능을 가진 틀을 만드는 것
- 실제 활동하는 개별 객체들은 이 틀에서 생성된 인스턴스(instance)
- 공통된 특성과 기능을 가진 틀을 만드는 것은 곧 새로운 타입을 만드는 행위
    - 아이유는 인스턴스다라는 표현이 모호한 이유 역시 마찬가지
    - 무슨 타입의 인스턴스인지를 알 수 없기 때문
        - ⇒ 아이유는 Singer의 인스턴스다가 정확한 표현
- 변수 name의 타입은 str 클래스다.
    
    ⇒ 변수 name은 str 클래스 인스턴스다.
    
    우리가 사용해왔던 데이터 타입은 사실 모두 클래스였다.
    
    ```python
    name = "Alice"
    print(type(name))  # <class 'str'> 
    
    print(help(str))
    """
    Help on class str in module builtins:
    
    class str(object)
     |  str(object='') -> str
     |  str(bytes_or_buffer[, encoding[, errors]]) -> str
     |
     |  Create a new string object from the given object. If encoding or
     |  errors is specified, then the object must expose a data buffer
     |  that will be decoded using the given encoding and error handler.
     |  Otherwise, returns the result of object.__str__() (if defined)
     |  or repr(object).
     |  encoding defaults to sys.getdefaultencoding().
     |  errors defaults to 'strict'.
     |
     |  Methods defined here:
     |
     |  __add__(self, value, /)
     |      Return self+value.
     |
     |  __contains__(self, key, /)
     |      Return key in self.
     |
     |  __eq__(self, value, /)
     |      Return self==value.
     |
     |  __format__(self, format_spec, /)
     |      Return a formatted version of the string as described by format_spec.
     """
    ```
    

### `''` , `'hello'` , `'파이썬'`

- 문자열 타입(클래스)의 객체(인스턴스)

### `[1, 2, 3]` , `[1]` , `[]` , `['HI']`

- 문자열 타입(클래스)의 객체(인스턴스)

### `"Hello".upper()`

- 문자열.대문자로()
- 객체.행동()
- 인스턴스.메서드()

## 클래스 구성요소

### 생성자 메서드

- 인스턴스 생성 시 자동 호출되는 특별한 메서드
- `__init__`  이라는 이름의 메서드로 정의
- 인스턴스 변수의 초기화 담당

### 인스턴스 변수(속성)

- 각 인스턴스 별 고유한 속성
- self.변수명 형태로 정의
- 인스턴스 마다 독립적인 값 유지

### 클래스 변수(속성) - var instance

- 모든 인스턴스가 공유하는 속성
- 클래스 내부에서 직접 정의

## 클래스 변수와 인스턴스 변수

### 클래스 변수와 인스턴스 변수

- 클래스 변수와 동일한 이름으로 인스턴스 변수 생성시
클래스 변수가 아닌 인스턴스 변수에 먼저 참조하게 됨
    
    ```python
    class Circle:
        pi = 3.14
    
        def __init__(self, radius):
            self.radius = radius
    
    c1 = Circle(5)
    c2 = Circle(10)
    
    # c1이 본인 인스턴스 변수 pi를 생성 # 안좋은 설
    c1.pi = 100
    print(c1.pi) # 100
    
    # c2가 본인 인스턴스 변수 new_pi를 생성
    c2.new_pi = 100
    print(c2.pi) # 3.14
    print(c2.new_pi) # 100
    ```
    

# 메서드

### 메서드(Method)

- 클래스 내부에 정의된 함수로 해당 객체가 어떻게 동작할 지를 정의
- 궁극적으로는 함수 → 근데 이제 클래스 안에 정의된

### 메서드 종류

1. 인스턴스 메서드
2. 클래스 메서드
3. 스태틱 메서드

## 인스턴스 메서드

### 인스턴스 메서드(instance method)

- 인스턴스의 상태를 조작하거나 동작을 수행
- 인스턴스마다 독립적으로 행동할 수 있게 만드는 것이 인스턴스 메서드
- 지금까지 배운 모든 데이터 타입 별 메서드들이 이에 해당

### 인스턴스 메서드 구조

- 클래스 내부에 정의되는 메서드의 기본
- 반드시 첫 번째 인자로 **인스턴스 자신(self)**을 받음
    - self는 매개변수 이름일 뿐이며 다른 이름으로 설정 가능 하지만 다른 이름을 사용하지 않을 것을 강력히 권
- 인스턴스의 속성에 접근하거나 변경이 가능

### self 동작 원리

- upper 메서드를 사용해 문자열 ‘hello’를 대문자로 변경하기
    
    ```python
    'hello'.upper()
    ```
    
- 하지만 실제 파이썬 내부 동작은 다음과 같이 진행됨
    
    ```python
    str.upper('hello')
    ```
    
- str 클래스가 upper 메서드를 호출했고, 그 첫 번째 인자로 문자열 인스턴스가 들어간 것
- `'hello'.upper()` 은 `str.upper('hello')` 를 객체 지향 방식의 메서드로 호출하는 단축형 호출
    
    ⇒ ‘hello’라는 문자열 객체가 단순히 어딘가의 함수로 들어가는 인자로 활용되는 것이 아닌
    객체 스스로 메서드를 호출하여 코드를 동작하는 객체 지향적인 표현인 것
    

### 인스턴스 메서드 활용

```python
class Counter:
    def __init__(self):
        self.count = 0
    # 인스턴스 메서드
    def increment(self) :
        self.count += 1
    pass

# 인스턴스 메서드 호출
c1 = Counter()
c2 = Counter()

c1.increment()

print(c1.count)
print(c2.count)

```

### 생성자 메서드(constructor method)

- 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드
    
    ⇒ 인스턴스 변수들의 초기값을 설정
    
    - 초기값 없어도 동작 가능
        - bec. 파이썬 내부에서 알아서 생성
        - 다만 구성상 표기하는 것을 권장
    
    ```python
    class Person:
        # 생성자 메서드
        def __init__(self, name): # 초기값 없어도 동작 가능 -> 다만 구성상 표기하는 것을 권장
            # 왼쪽 name : 인스턴스 변수 name
            # 오른쪽 name : 생성자 메서드의 매개변수 이름
            self.name = name
            print('인스턴스가 생성되었습니다.')
    
        def greeting(self):
            print(f'안녕하세요 {self.name}입니다.')
    
    person1 = Person("지민") # 인스턴스가 생성되었습니다.
    person1.greeting() # 안녕하세요 지민입니다.
    
    person1 = Person("지수") # 인스턴스가 생성되었습니다.
    ```
    

## 클래스 메서드

### 클래스 메서드(class method)

- 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행합니다.
- `@classmethod` 를 사용하면 클래스 자체가 호출할 수 있고,
그 안에서 클래스 변수를 변경하거나 전체 동작을 정의할 수 있습니다.

### 클래스 메서드 구조

- `@classmethod`  **데코레이터**를 사용하여 정의
    - 데코레이터를 보고 인스턴스 메서드와 구별 가능
- 호출 시, 첫 번째 인자로 해당 메서드를 호출하는 클래스(cls)가 전달됨
    - cls를 다른 이름으로 설정해도 되나 다른 이름을 사용하지 않을 것을 강력히 권
- 클래스를 인자로 받아 클래스 속성을 변경하거나 읽는 데 사용

### 클래스 메서드 활용

- `Person.increase_population()`  vs `Person.population += 1`
    - 같은 역할을 하지만 생성자 메서드는 인스턴스 메서드이며 초기화를 위한 메서드이기 때문에 설계적으로 권장되지 않음
    - 기능이 제대로 분리되어야 함

```python
class Person:
    population = 0

    def __init__(self, name):
        self.name = name
        Person.increase_population()
        # Person.population += 1도 같은 역할을 하지만 생성자 메서드는 인스턴스 메서드이며 초기화를 위한 메서드이기 때문에 설계적으로 권장되지 않음 == 기능이 제대로 분리되어야 함

    # 클래스 메서드
    @classmethod
    def increase_population(cls) :
        cls.population += 1
        

# 인스턴스 생성
person1 = Person('Alice')
person2 = Person('Bob')

# 클래스 변수 접근
print(Person.population)  # 2

```

## 스태틱 메서드

### 스태틱(정적) 메서드 (static method)

- 클래스, 인스턴스와 상관없이 독립저긍로 동작하는 메서드
- `@staticmethod` 를 사용하면 클래스 내부에 있지만 어떤 객체와도 관계없이 동작하는 메서드를 만들 수 있음

### 스태틱 메서드 구조

- `@staticmethod`  데코레이터를 사용하여 정의
- 호출 시 자동으로 전달 받는 인자가 없음 (self, cls를 받지 않음)
- 인스턴스나 클래스 속성에 직접 접근하지 않는 ‘도우미 함수’와 비슷한 역할
    - 아주 단순한 연산 같은 단일 함수에 사용

### 스태틱 메서드 활용

- 인스턴스는 인스턴스 메서드하나, 클래스 메서드는 클래스메서드, 정적 메서드 두개 씀

```python
class MathUtils:
    # 정적 메서드
    # 클래스나 인스턴스에 의존하지 않고 독립적으로 동작
    # 정적 메서드는 클래스나 인스턴스의 상태를 변경하지 않음
    @staticmethod
    def add (a, b) :
        return a + b
    pass

# 정적 메서드 호출
print(MathUtils.add(3, 5))
```

## 메서드 활용

## 메서드 정리

- 인스턴스 메서드
    - 인스턴스의 상태를 변경하거나, 해당 인스턴스의 특정 동작을 수행
- 클래스 메서드
    - 인스턴스의 상태에 의존하지 않는 기능을 정의
    - 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행
- 스태틱 메서드
    - 클래스 및 인스턴스와 관련이 없는 일반적인 기능을 수행

### 누가 어떤 메서드를 사용해야 할까

- 클래스가 사용해야 할 것
    - 클래스 메서드
    - 스태틱 메서드
        - 클래스는 모든 메서드를 호출할 수 있지만(기능적으로 막혀있지 않음) 정해진 것 만 해야 함
- 인스턴스가 사용해야 할 것
    - 인스턴스 메서드
        - 클래스는 모든 메서드를 호출할 수 있지만(기능적으로 막혀있지 않음) 정해진 것 만 해야 함
- 할 수 있다 ≠ 써도 된다
    - 각자의 메서드는 OOP 패러다임에 따라 명확한 목적에 맞춰 설계된 것이기 때문에
    클래스와 인스턴스 각각 올바른 메서드만 사용한다 !

# 참고

## 클래스와 인스턴스 간 이름 공간

- 클래스를 정의하면, 클래스와 해당하는 이름 공간 생성
- 인스턴스를 만들면, 인스턴스 객체가 생성되고 독립적인 이름 공간 생ㅅ ㅓㅇ
- 인스턴스에서 특정 속성에 접근하면 인스턴스 → 클래스 순으로 탐색
- TIP
    - 같은 클래스로 만든 인스턴스라도 서로 다른 이름 공간을 가지므로
    인스턴스 간 변수 값이 영향을 주고 받지 않음
    - 중복될 경우 인스턴스 값이 우선

### 독립적인 이름공간을 가지는 이점

- 각 인스턴스는 독립적인 메모리 공간을 가지며, 클래스와 다른 인스턴스 간에는 서로의 데이터나 상태에 지겆ㅂ적인 접근이 불가능
- 객체 지향 프로그래밍의 중요한 특성 중 하나로, 클래스와 인스턴스를 모듈화하고 각각의 객체가 독립적으로 동작하도록 보장
- 이를 통해 클래스와 인스턴스는 다른 객체들과의 상호작용에서 서로 충돌이나 영향을 주지 않으면서 독립적ㅇ르ㅗ 동작할 수 있음
- 코드의 가독성, 유지보수성, 재사용성을 높이는 데 도움을 줌

## 매직 메서드

- Double underscore(`__`)가 있는 메서드는 특수한 동작을 위해 만들어진 메서드
- 인스턴스 메서드
- **특정 상황에 자동으로 호출됨**
- 스페셜 메서드 혹은 매직 메서드라고 불림
- 예시
    
    ```python
    print(dir(int))
    # 실제로 int클래스에 dir을 사용해보면 수많은 매직 메소드가 반겨준다.
    ['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__', '__delattr__', 
    '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__',
    '__format__', '__ge__', '__getattribute__', '__getnewargs__', '__gt__', '__hash__', 
    '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__le__',
     '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', 
    '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__',
     '__repr__', '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__', '__round__',
     '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__',
     '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__',
     'as_integer_ratio', 'bit_count', 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag', 
    'numerator', 'real', 'to_bytes']
    ```
    

### 매직메서드 `__str__`  예시

[파이썬(python) - 매직 메소드(Magic method)](https://tibetsandfox.tistory.com/42)

- `__str__`
    - 내장함수 print에 의해 호출되어 객체 출력을 문자열 표현으로 변경

## 데코레이터

- 다른 함수의 코드를 유지한 채로 수정하거나 확장하기 위해 사용되는 함수
    
    ```python
    # 데코레이터 정의
    def my_decorator(func):
        def wrapper():
            # 함수 실행 전에 수행할 작업
            print('함수 실행 전')
            # 원본 함수 호출
            result = func()
            # 함수 실행 후에 수행할 작업
            print('함수 실행 후')
            return result
    
        return wrapper
    
    # 데코레이터 사용
    @my_decorator
    def my_function():
        print('원본 함수 실행')
    
    ```