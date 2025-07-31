# 상속

## 상속의 기본 개념

### 상속(Inheritance) : 한 클래스(부모)의 속성과 메서드를 다른 클래스(자식)가 물려받는 것

- 부모 클래스와 자식 클래스 간의 상하 관계가 형성되고, 위쪽에 있는 부모 클래스가 본인의 속성과 메서들르 아래 쪽에 있는 자식에게 넘겨주는 것이 상속
- ⇒ 속성과 메서드를 자식에게 넘겨주는 과정을 상속 과정이라고 함

### 상속이 필요한 이유

1. 코드 재사용
    1. 상속을 통해 기존 클래스의 속성과 메서들르 재사용할 수 있음
    2. 기존 클래스를 수정하지 않고도 기능을 확장할 수 있음
2. 계층 구조
    1. 상속을 통해 클래스 간의 계층 구조를 형성할 수 있음
    2. 부모 클래스와 자식 클래스 간의 관계를 표현하고, 더 구체적인 클래스를 만들 수 있음
3. 유지 보수의 용이성
    1. 상ㅅ ㅗㄱ을 통해 기존 클래스의 수정이 필요한 경우, 해당 클래스만 수정하면 되므로 유지보수가 용이해짐
    2. 코드의 일관성을 유지하고, 수정이 필요한 범위를 최소화할 수 있음

### 상속 예시

- 클래스의 상속개념 다이어그램 예시
    - 만약 RPG 게임을 구성한ㄴ다고 가정해보면
        - 직업군이 마법사, 전사 ,… 여러 가지 있을 거고 중복이 되는 공통점이 있을 거임
            - 예를 들면, 돈/레벨/공격/수비/이동 등 각자 가진 속성이나 행동이 모든 직업에 중복됨
            - ⇒ 캐릭터라는 부모클래스를 만들고, 전사, 마법사라는 자식 클래스를 만들 수 있음 → 자식마다 추가 기능만 구현하면 되는 것
- 상속 예시
    - Animal(eat) → Dog(eat, bark)
        
        ```python
        class Animal:
            def eat(self):
                print('먹는 중')
        
        class Dog (Animal):
            def __init__(self):
                super().__init__()
            def bark(self) :
                print('멍멍')
        
        my_dog = Dog()
        my_dog.eat()
        my_dog.bark()
        ```
        

## 클래스 상속

### 상속 없이 구현하는 경우

- 상속이 없이 구현하는 경우 학생/교수 정보를 별도로 표현하기 어려움
- Person class만을 사용하는 경우 학생과 교수가 가지는 각각의 고유한 속성을 표현하기 어려움. 나이와 이름 만으로는 직업 정보를 나타낼 수 없음
- 클래스를 각각 분리한다면 메서드가 중복으로 정의될 수 있어 구조적으로 좋지 않음

```python
# 상속 없는 경우 - 1
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):
        print(f'반갑습니다. {self.name}입니다.')

s1 = Person('김학생', 23)
s1.talk()  # 반갑습니다. 김학생입니다.

p1 = Person('박교수', 59)
p1.talk()  # 반갑습니다. 박교수입니다.
```

```python

# 상속 없는 경우 - 2
class Professor:
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department

    def talk(self):  # 중복
        print(f'반갑습니다. {self.name}입니다.')

class Student:
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa

    def talk(self):  # 중복
        print(f'반갑습니다. {self.name}입니다.')
```

### 상속을 사용한 계층 구조 변경

```python
# 상속을 사용한 계층구조 변경
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):  # 메서드 재사용
        print(f'반갑습니다. {self.name}입니다.')

class Professor(Person):
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department
    

class Student(Person):
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa

# 부모 Person 클래스의 talk 메서드를 활용
p1 = Professor('김교수', 50, '컴퓨터공학')
p1.talk()
# 부모 Person 클래스의 talk 메서드를 활용
s1 = Student('김학생', 20, 4.0)
s1.talk()

```

## 메서드 오버라이딩

### 메서드 오버라이딩(Method Overriding)

- 부모 클래스의 메서드를 같은 이름, 같은 파라미터 구조로 재정의하는 것
- 자식 클래스에서 메서드를 다시 정의하면, 부모 클래스의 메서드 대신 자식 클래스의 메서드가 실행됨
- 오버라이딩은 동일한 이름과 매개변수를 사용하지만, 내부 동작을 원하는 대로 바꿀 수 있게 해줌
- 부모 클래스의 기능을 유지하면서도 일부 동작을 맞춤형으로 바꾸고 싶을 때 유용

### 메서드 오버라이딩 예시

- 자식 클래스가 부모 클래스의 메서드를 덮어써서 새로운 동작을 구현할 수 있음
- Animal class 를ㄹ 상속받은 Dog 클래스에서 eat 메서드를 다시 정의하는 것
    - 파라미터 구조를 바꿀 수도 있으나 !
    **가장 중요한 원칙: "파라미터 구조를 동일하게 유지하라"**
        - **왜 파라미터를 바꾸면 안 될까? (다형성)**
            - 파라미터 구조를 다르게 오버라이딩하면, 객체 지향 프로그래밍의 핵심 개념인 `다형성(Polymorphism)`을 위반하여 예기치 않은 오류를 유발합니다.
            - 다형성(Polymorphism)
                - 서로 다른 클래스의 객체가 **동일한 메서드 호출에 대해 각자의 방식대로 다르게 응답**하는 능력
                - 마치 우리가 여러 동물에게 "울어봐"라고 똑같이 명령했을 때, 개는 "멍멍", 고양이는 "야옹"처럼 **각자 다른 방식으로 행동**하는 것과 같음

### [참고] 오버로딩(Overloading)

- 같은 이름, 다른 파라미터를 가진 여러 메서드를 정의하는 것(파이썬은 미지원)
- 파이썬은 실제로 하나의 메서드를 인식하며 인자의 형태가 다르다는 이유로 메서드를 여러 개 구분하여 불러주지 않음

```python
# 오버로딩 (파이썬 미지원)
class Example:
    def do_something(self, x):
        print('첫 번째 do_something 메서드:', x)

    # 파이썬에서는 메서드가 "이름"이 같으면 앞선 정의를 덮어써버림
    def do_something(self, x, y):
        print('두 번째 do_something 메서드:', x, y)

example = Example()
# TypeError: do_something() missing 1 required positional argument: 'y'
example.do_something(10)

```

## 다중 상속

### 다중 상속

- 둘 이상의 상위 클래스로부터 여러 행동이나 특징을 상속받을 수 있음
- 상속 받은 모든 클래스의 요소를 활용 가능
- 중복된 속성이나 메서드가 있는 경우 **상속 순서에 의해 결정됨**
    - 상속 순서가 **빠른** (== `FirstChild( <**<부모클래스1>>**, <부모클래스2>)` ) 
    부모 클래스의 메서드를 참조하게 됨

### 다중 상속의 예시

```python
# 다중 상속 예시
class Person:
    def __init__(self, name):
        self.name = name

    def greeting(self):
        return f'안녕, {self.name}'

class Mom(Person):
    gene = 'XX'

    def swim(self):
        return '엄마가 수영'

class Dad(Person):
    gene = 'XY'

    def walk(self):
        return '아빠가 걷기'

class FirstChild(Dad, Mom): # 여기서 상속 순서가 정해짐
    def swim(self):
        return '첫째가 수영'

    def cry(self):
        return '첫째가 응애'

baby1 = FirstChild('아가')
print(baby1.cry())  # 첫째가 응애
print(baby1.swim())  # 첫째가 수영
print(baby1.walk())  # 아빠가 걷기
# print(baby1.gene)  # XY

```

### 다이아몬드 문제 (The diamond problem)

- 두 클래스 B와 C가 A에서 상속되고 클래스 D가 B와 C 모두에서 상속될 때 발생하는 모호함
- B와 C가 재정의한 메서드가 A에 있고 D가 이를 재정의하지 않은 경우라면
    - D는 B의 메서드 중 어떤 버전을 상속하는가?
    아니면 C의 메서드 버전을 상속하는가?
    
    ```python
    class A:
        def __init__(self):
            print('A Constructor')
    
    class B(A):
        def __init__(self):
            super().__init__()
            print('B Constructor')
    
    class C(A):
        def __init__(self):
            super().__init__()
            print('C Constructor')
    
    class D(B, C):
        def __init__(self):
            super().__init__()
            print('D Constructor')
    
    # [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
    print(D.mro())
    
    # (<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>)
    print(D.__mro__)
    
    ```
    

### 파이썬에서의 해결책

- MRO 알골리즘을 사용하여 클래스 목록을 생성
- \4/
- 부모 클래스로부터 상속된 속성을 정해진 내부 알고리즘에 ㄸ라ㅏ 검색
- 이 순서는 기본적으로 왼쪽에서 오른쪽으로 진행되며, 계층 구조에서 중복되는 클래스는 한 번만 확인
- 그래서, 속성이 D에서 발견되지 않으면, B에서 찾고, 거기에서도 발견되지 않으면, C에서 찾고, 이런 식으로 진행됨

### 메서드 결정 순서: MRO

- 파이썬이 메서드를 찾는 순서에 대한 규칙
- 메서드 결정 순서
- 파이썬은 미리 정해진 MRO를 통해 다중 상속 환경에서도 예측 가능한 방식으로 메서드 탐색이 이루어질 수 있도록 함

## super() 함수

### super()란?

- 메서드 해석 순서(MRO)에 따라, 현재 클래스의 부모(상위) 클래스의 메서드나 속성에 접근할 수 있게 해주는 내장 함수
- super()를 사용하면 직접 부모 클래스 이름을 적지 않아도 MRO에 따라 자동으로 올바른 메서드를 찾아 실행할 수 있음
- 다중 상소게어 supser()를 호출하면 상속 순서에 맞춰 여러 부모 클래스이 메서드를 순차적으로 실행할 수 있음
- 생성자나 오버라이딩 메서드에서 super()를 호출하며 ㄴ부모 클래스의 초기화나 로직을 그대로 활용 가능

### super() 특징

- 단순히 “부모 클래스이 메서드를 호출”하기 위한 용도 뿐만 아니라, 다중 상속이 있을 때도 올바른 순서에 따라 상위 클래스의 메서드를 찾아 실행하기 위해 super()를 사용

### super() 예시

- 단일 상속
    - Student 생성자에서 super().__init__()를 호출하면, Person 의 **`__init__**()` 메서드가 호출되어 name, age, number, email 속성을 초기화한 뒤 Student 고유의 student_id 속성을 추가
    - 이때 Person 클래스를 직접 명시하지 않고 super()를 사용하므로, 나중에 클래스 이름이 바뀌거나 상속 구조가 변경되어도 super() 호출 부분을 그대로 사용할 수 있어 유지보수성이 향상

```python
# 단일 상속

# super를 사용하지 않았을 때
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email

class Student(Person):
    def __init__(self, name, age, number, email, student_id):
        self.name = name
        self.age = age
        self.number = number
        self.email = email
        self.student_id = student_id

# super를 사용했을 때
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email

class Student(Person):
    def __init__(self, name, age, number, email, student_id):
        # super()를 통해 Person의 __init__ 메서드 호출
        pass
        self.student_id = student_id

```

- 다중 상속
    - Child 클래스는 ParentA, ParentB를 순서대로 상속
    - `print(ChildClass.mro())`  / `print(D.**mro**)`로 순서를 확인할 수 있음

```python
# 다중 상속
class ParentA:
    def __init__(self):
        # super().__init__()
        self.value_a = 'ParentA'

    def show_value(self):
        print(f'Value from ParentA: {self.value_a}')

class ParentB:
    def __init__(self):
        self.value_b = 'ParentB'

    def show_value(self):
        print(f'Value from ParentB: {self.value_b}')

class Child(ParentA, ParentB):
    def __init__(self):
        super().__init__()  # ParentA 클래스의 __init__ 메서드 호출
        self.value_c = 'Child'

    def show_value(self):
        super().show_value()  # ParentA 클래스의 show_value 메서드 호출
        print(f'Value from Child: {self.value_c}')

child = Child()
child.show_value()
"""
Value from ParentA: ParentA
Value from Child: Child
"""

print(child.value_c)  # Child
print(child.value_a)  # ParentA
```

### 다중 상속 구조에서의 super() 함수

- MRO(메서드 해석 순서)에 따라 각 클래스의 메스들 찾아가기 때문에,
단순히 직계 부모만이 아니라 다중 상속 관계에서도 적절한 상위 클래스의 메서드를 안전하게 호출할 수 있음
- 이를 통해 복잡한 상속 구조에서도 코드를 유연하고 깔끔하게 유지할 수 있음

### super() 정리

- super()를 사용할 때는 MRO를 잘 이해하고 있어야 함
- .__mro__ 또는 .mro()를 확인해 MRO 순서를 파악한 뒤
적절히 활용하는 연습을 하면, 보다 복잡한 상속 구조에서도 코드를 잘 관리할 수 있음

### MRO가 필요한 이유

- 부모 클래스들이 여러 번 엑세스 되지 않도록, 각 클래스에서 지정된 왼쪽에서 오른쪽으로 가는 순서를 보존하고,
각 부모를 오직 한 번만 호출하고,
부모들의 우선 순위에 영향을 주지 않으면서 서브 클래스를 만드는 단조적인 구조 형성

# 에러와 예외

## 디버깅

### 버그(bug) : 소프트웨어에서 발생하는 오류 또는 결함 프로그램의 예상된 동작과 실제 동작 사이의 불일치

### 디버깅(debugging) :  소프트웨어에서 발생하는 버그를 찾아내고 수정하는 과정

- 효과적인 디버깅을 위해 단계별로 코드를 실행하거나 로그를 출력해 프로그램 상태를 확인

## 에러

### 에러(Error) : 프로그램 실행 중에 발생하는 예외 상황

- 프로그램을 실행할 때 예상치 못한 문제가 발생하면 오류가 생김

### 파이썬의 에러 유형

- 문법 에러 (Syntax Error)
    - 프로그램의 구문이 올바르지 않은 경우 발생
- 예외 (Exception)
    - 프로그램 실행 중에 감지되는 에러

### 문법 에러 예시

- Invalid syntax (문법 오류)
- assign to literal (잘못된 할당)
- Unterminated string literal
    - 보통 문자열이나 문장을 제대로 닫지 않은 상ㅇ태에서 줄 끝에 다다랐을 때 발생
- TIP :
    - 문법 에러는 코드 실행 이전에 발생하므로, 에디터에서 제공하는 밑줄, 색상, 자동완성 등을 적극 활용해 미리 감지하기

### 

## 예외

### 예외(Exception) :프로그램 실행 중에 감지되는 에러

- 예외는 프로그램이 잘못된 동작을 시도할 때 자동으로 감지
- 이런 상황을 처리하지 않으면 프로그램은 즉시 종료됨

### 내장 예외 (Built-in Exception) : 예외 상황을 나타내는 예외 클래스들

- 내장 예외는 파이썬에서 이미 정의되어 있으며, ㅓ특정 예외 상황에 대한 처리를 위해 사용
- 예) ZeroDivisionError , FileNotFoundError

- ZeroDivisionError
- NameError
- TypeError
    - 타입 불일치
    - 인자 누락
    - 인자 초과
    - 인자 타입 불일치
- ValueError
- IndexError
- KeyError
- ModuleNotFoundError
- ImportError
- KeyboardInterrupt
    - 사용자가 Ctrl - c 또는 Delete 를 누를 때 발생
    - 무한 루프 시 강제 종료
- IndentationError
    - 잘못된 들여쓰기와 관련된 문법 오류
- FileNotFoundError

# 예외 처리

### 예외 처리 (Exception Handling) : 예외가 발생했을 때 프로그램이 비정상적으로 종료되지 않고, 적절하게 처리할 수 있도록 하는 방법

- 예외 처리를 통해 오류가 발생해도 프로그램의 흐름을 안전하게 이어갈 수 있음
- Python 에서는 try. except 구문을 사용해 특정 예외를 잡아내고 원하는 동작을 수행할 수 있음
- 예외 처리를 구현하면 프로그램 사용자에게 오류 메시지를 보여주거나 대체 로직을 실행할 수 있음

### 예외 처리 사용 구문

- **try** : 예외가 발생할 수 있는 코드 작성
- **except** : 예외가 발생했을 때 실행할 코드 작성
- else(optional) : 예외가 발생하지 않을 때 실행할 코드 작성
- finally(optional) : 예외 발생 여부와 상관없이 항상 실행할 코드 작성

## try-except 구조

### try-except 구조

- try 블록 안에는 예외가 발생할 수 있는 코드를 작성
- except  블록 안에는 예외가 발생했을 때 처리할 코드를 작성
- 예외가 발생하면 프로그램 흐름은  try  블록을 빠져나와 해당 예외에 대응하는  except 블록으로 이동

### 예외 처리 예시

- 오류가 날 만한 코드 예외 처리

```
# try-except
try :
    result = 10 /0

except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
```

- 사용자 입력 값에 대한 예외 처리

```python
# 오류 메시지 확인
num = int(input('숫자를 입력하세요 : '))
# ValueError: invalid literal for int() with base 10: 'd'

# 오류 메시지 사용하여 예외 처리
try : 
    num = int(input('숫자를 입력하세요 : '))
except ValueError:
    print('숫자를 입력하라구요.!!!')
```

## 복수 예외 처리

### 복수 예외 처리 연습

- 100을 사용자가 입력한 값으로 나누고 출력하는 코드
    - 먼저, 발생가능한 에러가 무엇인지 예상해보기
    - 예외 조건은 `except (예외조건1 ,예외조건2, ... )`  형식으로 작성하거나
    `except (예외조건) : … exept (예외조건) : …` 방식으로 여러 중첩 구문 작성
    
    ```python
    # 복수 예외처리
    try:
        num = int(input('100을 나눌 값을 입력하시오 : '))
        print(100 / num)
    except (ValueError, ZeroDivisionError):
        print('제대로 입력해주세요.')
    
    try:
        num = int(input('100을 나눌 값을 입력하시오 : '))
        print(100 / num)
    except ValueError:
        print('숫자를 넣어주세요.')
    except ZeroDivisionError:
        print('0으로 나눌 수 없습니다.')
    except:
        print('에러가 발생했습니다.')
    
    ```
    

## else & finally

### else & finally

- else 블록은 예외가 발생하지 않았을 때 추가 작업을 진행
- finally 블록은 예외 발생 여부와 상관없이 항상 실행할 코드를 작성

```python
try:
    x = int(input('숫자를 입력하세요: '))
    y = 10 / x
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
except ValueError:
    print('유효한 숫자가 아닙니다.')
else:
    print(f'결과: {y}')
finally:
    print('프로그램이 종료되었습니다.')

```

# 참고

## 예외 처리 주의사항

### 내장 예외의 상속 계층 구조 주의

- 아래와 같이 예외를 작성하면 코드는 2번째 except 절에 이후로 도달하지 못함
- except Exception이 모든 예외를 먼저 가로채기 때문에, 그 아래에 있는 ZeroDivisionError 전용 처리 코드는 절대 실행되지 않음
    - 내장 예외 **클래스**는 **상속 계층구조**를 가지기 때문에  except 절로 분기 시 **반드시 하위 클래스를 먼저 확인할 수 있도록 작성**해야 함
        - 항상 범용적인 예외 처리는 마지막에 두어야 함
            - 가장 구체적인 예외부터 처리하고, 마지막에 범용 예외를 처리하도록 순서를 배치

```python
# 나쁜 코드
try:
    num = int(input('100으로 나눌 값을 입력하시오 : '))
    print(100 / num)
except Exception:
    print('숫자를 넣어주세요.')
# ZeroDivisionError는 Exception의 하위 클래스이므로 Exception보다 먼저 작성해야 함
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
except:
    print('에러가 발생하였습니다.')

```

```python
# 옳은 코드
# 가장 구체적인 예외부터 처리하고, 마지막에 범용 예외를 처리하도록 순서를 배치
try:
    num = int(input('100으로 나눌 값을 입력하시오 : '))
    print(100 / num)
# 1) 구체적인 예외부터
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
except ValueError:
    print('숫자를 넣어주세요.')
# 2) 마지막에 광범위한 예외(Exception)
except Exception:
    print('에러가 발생하였습니다.')
```

- 그렇다면 except: 가 더 상위 클래스일까 except Exception:이 더 상위클래스일까?
    - default ‘except:’는 무조건 마지막에 선언되어야 함.
        - 그 이유는?

```python
# SyntaxError: default 'except:' must be last
try:
    num = int(input('100으로 나눌 값을 입력하시오 : '))
    print(100 / num)
except :
    print('숫자를 넣어주세요.')
# ZeroDivisionError는 Exception의 하위 클래스이므로 Exception보다 먼저 작성해야 함
except ZeroDivisionError:
    print('0으로 나눌 수 없습니다.')
except Exception:
    print('에러가 발생하였습니다.')

```

### ✅ `except:`는 **가장 상위 개념**(=모든 예외의 포괄)이야.

그런데 **"왜 SyntaxError로 막는가"**에 대한 의문은 아주 날카로운 질문이야.

---

### ❓ 그냥 except에서 끝나면 되는 거 아닌가?

예를 들어:

```python
python
복사편집
try:
    1 / 0
except:
    print("예외 처리 완료")
except ZeroDivisionError:
    print("0으로 나눴음")

```

이런 식으로 쓴다면, 파이썬 입장에선 이렇게 생각함:

> “위에서 이미 모든 예외를 잡았는데, 밑에 ZeroDivisionError는 절대 도달할 수 없음.
> 
> 
> → 의미 없는 코드임 → 문법적으로 **금지**시켜야겠다!”
> 

---

### 💥 그래서 `SyntaxError`가 발생해

파이썬 컴파일러는 단순히 “경고”만 주는 게 아니라,

**"논리적으로 절대 실행될 수 없는 코드"는 문법 자체로 막는 규칙**을 가지고 있어.

이건 다음과 같은 상황과 비슷해:

```python
python
복사편집
def test():
    return 1
    return 2   # ❌ 여기도 SyntaxError는 아니지만 dead code (실행 불가)

```

> except: 이후에 오는 except Exception:도 똑같이 dead code로 간주돼.
> 
> 
> 단, 이건 **런타임이 아니라 문법 오류(SyntaxError)**로 막음.
> 
> 왜냐면 예외처리는 **순서를 반드시 명시적으로 정해줘야** 하기 때문에.
> 

---

### ✅ 파이썬이 의도적으로 이렇게 설계한 이유는?

- 개발자가 **순서를 실수로 잘못 쓸 수 있기 때문에**
- **불필요한 코드/비효율적인 예외 처리 방지**를 위해
- **코드의 명확성과 안전성을 높이기 위해**

---

### 🧠 정리하자면

| 구분 | 설명 |
| --- | --- |
| `except:` | **모든 예외를 잡음** (`BaseException` 포함) |
| `except Exception:` | 대부분의 예외를 잡지만, 시스템 관련은 제외 |
| `except:`가 먼저 나오면? | **뒤는 절대 실행 안 됨 → SyntaxError 발생** |
| 왜 SyntaxError인가? | **파이썬의 명시적 설계 기준**에 따라, 이런 구조는 아예 문법적으로 금지됨 |

## 예외 객체 다루기

### as 키워드

- 예외 객체  : 예외가 발생했을 때 예외에 대한 정보를 담고 잇는 객체
- except 블록에서의 예외 객체를 받아 상세한 예외 정보를 활용 가능

### try-except와 if-else

- try-except와 if-else를 함께 사용할 수 있음

### EAFP & LBYL

- EAFP : Easier to Ask for Forgiveness than Permisison
    - 예외 처리를 중심으로 코드를 작성하는 접근 방식
    - try - except
    - 일단 실행하고 예외를 처리
    - 예외 상황을 예측하기 어려운 경우에 유용
- LBYL : Look Before You Leap
    - 값 검사를 중심으로 코드를 작성하는 접근 방식
    - if -else
    - 실행하기 전에 조건을 검사
    - 예외 상황을 미리 방지하고 싶을 때 유용
    - 

## 클래스의 의미와 활용

### 클래스 사용의 효능

- 왜 클래스를 배웠을까?
    - 프로그램의 규모가 커지면 서로 관련있는 정보와 기능을 따로따로 관리하기가 점점 어려워짐
    - 클래스를 사용하면 관련된 데이터와 기능을 한 덩어리로 묶어 구조를 명확히 할 수 있음
    - 이로써 작성한 코드가 훨씬 깔끔해지고 나중에 수정 및 확장 시 쉽고 안전해짐

### 알고리즘 문제풀이와  OOP

- 알고리즘 문제를 풀 때는 크게 필요하지 않을 수 있음
- 하지만 크거나 복잡한 프로그램 개발 시 클래스를 통해 구조를 잘 짜는 것이 필수가 됨