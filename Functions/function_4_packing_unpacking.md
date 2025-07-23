# Packing & Unpacking

## Packing

### 패킹(Packing)

- 여러 개의 데이터를 하나의 컬렉션으로 모아 담는 과정
- 여러 개의 값을 하나의 튜플로 묶는 파이썬의 기본 동작
- 함수를 **‘정의’**할 때 사용

### `*` 을 활용한 패킹 (함수 매개변수 작성 시)

- 남는 위치 인자들을 튜플로 묶기
- `*` 를 붙인 매개변수가 남는 위치 인자들을 모두 모아 하나의 튜플로 만듦

```python
# ‘*’ 을 활용한 패킹 (함수 매개변수 작성 시)
def my_func(*args): **# 이 args라는 매개변수 이름은 바꿔도 되지만 굳이 바꾸지 않음**
    print(args)  # (1, 2, 3, 4, 5)
    print(type(args))  # <class 'tuple'>

my_func(1, 2, 3, 4, 5)
```

### `**` 을 활용한 패킹 (함수 매개변수 작성 시)

- 남는 키워드 인자들을 딕셔너리로 묶기
- `**`를 붙인 매개변수가 남는 키워드 인자들을 모두 모아 하나의 딕셔너리로 만듦

```python
# ‘**’ 을 활용한 패킹 (함수 매개변수 작성 시)
def my_func2(**kwargs): **# 이 kwargs라는 매개변수 이름은 바꿔도 되지만 굳이 바꾸지 않음**
    print(kwargs)  # {'a': 1, 'b': 2, 'c': 3}
    print(type(kwargs))  # <class 'dict’>

my_func2(a=1, b=2, c=3)
```

### `print()` 함수의 패킹 예시

- `print()` 함수에서 임의의 가변 인자를 작성할 수 있었던 이유
    - 인자 개수에 상관 없이 튜플 하나로 패킹 되어서 내부에서 처리
    - `print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)`
        - `end =`  인자 수정하면 다양하게 print 방식 변경 가능
        - `objects`를 텍스트 스트림 `file`로 인쇄하는데 `sep`로 구분되고 `end`를 뒤에 붙입니다. 있다면, `sep`, `end`, `file` 및 `flush`는 반드시 키워드 인자로 제공해야 합니다.

## UnPacking

### 언패킹(Unpacking)

- 컬렉션에 담겨 있는 데이터들을 개별 요소로 펼쳐 놓는 과정
- ‘시퀀스 언패킹(Sequence Unpacking)’ 또는 ‘다중 할당(Multiple Assignment)’ 이라고 부름
- 함수를 **‘호출’**할 때 사용

```python
packed_values = 1, 2, 3, 4, 5

# 언패킹
a, b, c, d, e = packed_values
print(a, b, c, d, e)  # 1 2 3 4 5

```

### `*` 을 활용한 언패킹 (함수 인자 전달)

```python
# ‘*’ 을 활용한 언패킹 (함수 인자 전달)
def my_function(x, y, z):
    print(x, y, z)

names = ['alice', 'jane', 'peter']
my_function(*names)  # alice jane peter

names = ['alice', 'jane']
my_function(*names)  # alice jane
# TypeError: my_function() missing 1 required positional argument: 'z'
```

### `**` 을 활용한 언패킹 ( 딕셔너리 → 함수 키워드 인자)

```python
# ‘**’을 활용한 언패킹 (딕셔너리 -> 함수 키워드 인자)
def my_function(x, y, z):
    print(x, y, z)

my_dict = {'x': 1, 'y': 2, 'z': 3}
my_function(**my_dict)  # 1 2 3
```