## global 키워드

### 이론 ‘global’ 키워드

- 변수의 scope를 전역 범위로 지정하기 위해 사용
- 일반적로 함수 내에서 전역 변수를 수정하려는 경우에 사용

```python
num = 0  # 전역 변수

def increment():
    global num  # num를 전역 변수로 선언
    num += 1

print(num)  # 0

increment()

print(num)  # '1
```

### ‘global’ 키워드 주의사항 -1

- `global` 키워드 선언전에 참조 불가

```python
# global 키워드 선언전에참조불가
num = 0

def increment():
    # SyntaxError: name 'num' is used # prior to global declaration
    print(num)
    global num
    num += 1
```

### ‘global’ 키워드 주의사항 -2

- 매개변수에는 global 키워드 사용 불가

```python
# 매개변수에는 global 키워드 사용불가
num = 0

def increment(num):
    # "num" is assigned before global # declaration
    global num
    num += 1

```