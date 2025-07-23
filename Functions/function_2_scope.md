## 함수와 Scope

### Python의 범위(Scope)

- 함수는 코드 내부에 locla scope를 생성하며, 그 외의 공간인 global scope로 구분

### 범위와 변수 관계

- scope
    - global scope : 코드 어디에서든 참조할 수 있는 공간
    - local scope : 함수가 만든 scope(함수 내부에서만 참조 가능)
- variable
    - global variable : global scope에 정의된 변수
    - local variable : local scope에 정의된 변수

### Scope 예시

- num은 local scope에 존재하기 때문에 global scope에서 사용할 수 없음
- 이는 변수의 **수명주기**와 연관이 있음

```python
# 1. Scope 예시
def func():
    num = 20
    print('local', num)  # local 20

func()
print('global', num)  # NameError: name 'num' is not defined
# 2. Scope 예
def func():
    global num
    num = 20
    print('local', num)  # local 20

```

### 변수 수명주기(lifecycle)

- 변수의 수명주기는 변수가 선언되는 위치와 scope에 따라 결정됨
    1. built-in scope
        - 파이썬이 실행된 이후부터 영원히 유지
    2. global scope
        - 모듈이 호출된 시점 이후 혹은 * **인터프리터**가 끝날 때까지 유지
            - *** 프로그래밍 언어 소스 코드를 한 줄씩 읽어 즉시 실행하는 프로그램 또는 환경**
    3. local scope
        - 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

### 이름 검색 규칙(Name Resolution)

- 파이썬에서 사용되는 이름(식별자)들은 특정한 이름공간(namespace)에 저장되어 있음
- 아래와 같은 순서로 이름을 찾아 나가며, LEGB Rule이라고 부름
    1. Local scope : 지역 범위(현재 작업 중인 범위)
    2. Enclosed scope : 지역 범위 한 단계 위 범위
    3. Global scope : 최상단에 위치한 범위
    4. Built-in scope : 모든 것을 담고 있는 범위
- 함수 내에서는 바깥 Scope의 변수에 접근 가능하나 수정은 할 수 없음

### LEGB Rule 예시

- sum이라는 이름을 global scope에서 사용함으로써, 기존 built-in scope에 있던 내장함수 sum을 사용하지 못하게 됨
    - sum을 참조 시 LEGB Rule에 따라 global에서 먼저 찾기 때문

```python
# 내장 함수 sum의 이름을 사용해버려서 오류가 발생하는 예시
print(sum)  # <built-in function sum>
print(sum(range(3)))  # 3
sum = 5
print(sum)  # 5
print(sum(range(3)))  # TypeError: 'int' object is not callable

```

- 코드 추가 설명
    - sum 변수 객체 삭제를 위해 del sum을 입력 후 진행