## 반복문(Loop Statement)

### 반복문의 정의

- 주어진 코드 블록을 여러 번 반복해서 실행하는 구문

### 반복문의 종류

- `for`문
    - 반복 가능(iterable)한 객체의 요소들을 반복하는데 주로 사용
    - 주로 반복 가능(iterable)한 객체 요소의 개수만큼 반복
    - 특징: 반복 횟숫가 정해져 있음
- `while` 문
    - while 조건이 참(True)인 동안 반복
    - 반복 횟수가 정해지지 않은 경우 주로 사용

## `for` statement

### `for` 반복문

- **반복 가능한(iterable) 객체**의 요소들을 반복하는 데 사용
- **반복 가능한 객체**의 요소 개수만큼 반복이 수행
    - 시퀀스 자료형 (list, tuple, str) 뿐만 아니라 비 시퀀스 자료형(dict, set)도 반복 가능한 객체임

### `for` 문 작동 원리

- 더 이상 반복 변수에 할당할 값이 없으면 반복 종료
- `for item(반복할 변수-단수형으로 작성) in 반복할 자료형 변수 :`

```python
# for문 기본
students = ['alice', 'harry', 'bob']

for student in students :
    print(student)
```

### 문자열 순회

- 문자열은 문자로 구성된 시퀀스 자료형
- 문자열 반복시 **문자**가 **반복 변수에 할당**되어 반복 수행
    
    ```python
    # 문자열 순회
    country = 'Korea'
    
    for char in country:
        print(char)
    ```
    

### range 순회

- 특정 숫자 범위만큼 반복을 하고 싶을 때 `range()` 함수를 사용
    
    ```python
    # range 순회
    for i in range(5):
        print(i)
    ```
    

### 딕셔너리 순회

- `dict` 자료형은 비시퀀스 자료형으로 반 순서가 보장되지 않음을 유의

```python
# dictionary 순회
my_dict = {
    'x': 10,
    'y': 20,
    'z': 30,
}

for key in my_dict:
    print(key)
    print(my_dict[key])

```

### 인덱스로 리스트 순회

- 리스트의 요소가 아닌 인덱스로 접근하여 해당 요소들을 변경하기
- 인덱스를 사용하면 리스트의 원하는 위치에 있는 값을 읽거나 변경할 수 있음

```python
# 인덱스 순회
numbers = [4, 6, 10, -8, 5]

for i in range(len(numbers)):
    numbers[i] = numbers[i] * 2

print(numbers) #[8, 12, 20, -16, 10]

```

### 중첩된 반복문

- 중첩된 반복문에서의 출력 예상해보기

```python
# 중첩 반복문
outers = ['A', 'B']
inners = ['c', 'd']

for outer in outers:
    for inner in inners:
        print(outer, inner)
```

### 중첩 리스트 순회

- 안쪽 리스트 요소에 접근하려면 바깥 리스트를 순회하면서 중첩 반복을 사용해 각 안쪽 반복을 수행
    
    ```python
    # 중첩 리스트 순회
    elements = [['A', 'B'], ['c', 'd']]
    
    # 1
    for elem in elements:
        print(elem)
    
    # 2
    for elem in elements:
        for item in elem:
            print(item)
    
    ```
    

## `while` statement

### `while` 반복문

- 주어진 조건식이 참(`True`)인 동안 코드를 반복해서 실행
- == 조건식이 거짓(`False`)이 될 때까지 반복해서 실행

### `while` 문의 반복 원리

- `while`의 조건식 확인
    - 조건식이 `True`면 코드 블록 실행
    - 조건식이 `Fals`e면 반복 종료
- 코드 블록이 실행이 마무리되면 다시 `while` 조건식 확인

### 사용자 입력에 따른 반복

- `while` 문을 사용한 특정 입력 값에 대한 종료 조건 활용하기
- `for`는 횟수의 관점이라면, `while`은 과정의 관점

### `while` 문의 특징

- 반드시 **종료 조건**이 필요
    - 종료 조건이 없는 경우 무한 반복에 빠지게 되어 원하는 동작을 하지 않게 되므로 반드시 종료 조건을 설정해야 함
- TIP
    - 조건이 언젠가는 반드시 False가 되도록 반복문 냅주에서 변수 값을 변화시키는게 좋음
    - `while` 문을 시작하기 전에 조건에서 사용할 변수를 반드시 초기화해야 오류 방지 가능
    - 예상치 못한 상황에 대비해 break 문을 활용하면 반복문을 안전하게 종료 가능

## `for` 와 `while` 정리

### `for`  반복문

- iterable 요소를 하나씩 순회하며 반복
- 반복 횟수가 명확하게 정해져 있는 경우 유용
    - 리스트, 튜플, 문자열 등과 같은 시퀀스 형식 처리할 경우
    - `range()` 함수를 사용해 일정 횟수 만큼 반복 작업을 수행할 경우

### `while` 반복문

- 주어진 조건식이 True인 동안 반복
- 반복 횟수가 불명확하거나 조건에 따라 반복을 종료해야 할 때 유용
    - 사용자의 입력을 받아 특정 조건이 충족될 때까지 반복하는 경우
    - 반복 횟수가 미리 정해져 있지 않고, 특정 조건이 만족될 때까지 반복해야 하는 경우

### Tip

- 문제의 반복 조건과 목적에 따라 더 적합한 반복문 선택이 중요
- 필요하다면 두 반복문을 중첩하거나 상황에 따라 자유롭게 바꿔 쓸 수 있음

## 반복 제어

### 반복 제어 이론

- `for`문과 `while`문은 매 반복마다 본문 내 모든 코드를 실행하지만 때때로 일부만 실행하는 것이 필요할 때가 있음

### 반복 제어 키워드

- `break` 키워드
    - 해당 키워드를 만나게 되면 남은 코드를 무시하고 반복 즉시 종료
    - 반복을 끝내야 할 명확한 조건이 있을 때 사용
    
    ```python
    # break 키워드 기본
    for i in range(10):
        if i == 5:
            break
        print(i)  # 0 1 2 3 4
    
    ```
    

- `continue` 키워드
    - 해당 키워드를 만나게 되면 다음 코드는 무시하고 다음 반복을 수행
    
    ```python
    # continue 키워드 기본
    for i in range(10):
        if i % 2 == 0:
            continue
        print(i)  # 1 3 5 7 9
    ```
    

- TIP
    - 반복 제어문은 반드시 반복문 내에서 사용해야 함
    - 중첩 반복문인 경우 해당 키워드가 작성된 코드 블록의 반복 흐름만 제어
    - 과도하게 사용하면 가독성이 떨어지므로 필요한 상황에서만 사용

### `break` 예시

- 리스트에서 첫번째 짝수만 찾은 후 반복 종료

```python
# break 키워드 예시 (for문)
# 리스트에서 첫번째 짝수만 찾은 후 반복 종료하기
numbers = [1, 3, 5, 6, 7, 9, 10, 11]
found_even = False

for num in numbers:
    if num % 2 == 0:
        print('첫 번째 짝수를 찾았습니다:', num)
        found_even = True
        break

if not found_even:
    print('짝수를 찾지 못했습니다')

```

```python
# break 키워드 예시 (while문)
# 프로그램 종료 조건 만들기
number = int(input('양의 정수를 입력해주세요.: '))

while number <= 0:
    if number == -9999:
        print('프로그램을 종료합니다.')
        break

    if number < 0:
        print('음수를 입력했습니다.')
    else:
        print('0은 양의 정수가 아닙니다.')

    number = int(input('양의 정수를 입력해주세요.: '))
print('잘했습니다!')

```

### `continue` 예시

- 리스트에서 홀수만 출력하기
    
    ```python
    # continue 키워드 예시
    # 리스트에서 홀수만 출력하기
    numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    for num in numbers:
        if num % 2 == 0:
            continue
        print(num)
    
    ```
    

### 빈 코드 블록 키워드

- `pass` 키워드
    - **아무 동작도 하지 않음**을 명시적으로 나타내는 키워드
    - 반복 제어가 아닌 코드의 **틀을 유지**하거나 **나중에 내용을 채우기 위한** 용도로 사용
    - **코드를 비워두면 오류가 발생**하기 때문에 **`pass`** 키워드를 사용함
    - 반복문 뿐만 아니라 함수, 조건문에서도 사용 가능

```python
while True :
	if conditon1:
		break
	elif contidion2:
		pass
	else :
		print('출력')
```

```python
if condition :
		pass
elif :
		pass
```

```python
def my_function() :
		pass # 없으면 오류 발생
```

### `for - else` , `while - else`

- `for` 루프가 `break` 를 만나 중단되지 않고, 끝까지 정상적으로 완료되었을 때만 `else` 블록이 실행
    - `break` 문을 만나 반복문이 종료되면 `else` 코드 블록은 실행되지 않음
    - `while - else` 문도 존재하며 동작 규칙도 동작 규칙도 '