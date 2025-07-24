## 유용한 내장 함수 `map` & `zip`

## `map` 함수

`map(function, iterable)` : 반ㅂ고 가능한 데이터구조(iterable)의 모든 요소에 `function` 을 적용하고, 그 결과 값들을 map object로 묶어서 반환

- `map object` : 결과를 하나씩 꺼내 쓸 수 있는 반복 가능한 객체 자료형. 전체 값을 확인하려면 list나 tuple로 형변환을 해줘야 함

### `map` 함수 활용

- SWEA 문제의 `input()`처럼 문자열 ‘1 2 3’이 입력되었을 때 활용 예시
    
    ```python
    numbers1 = input().split()
    print(numbers1)  # ['1', '2', '3']
    ```
    
    - `split()` 메서드
        - 문자열을 지정한 기준 문자를 기준으로 잘라서, 잘린 문자들을 리스트로 반환해주는 문자열 메서드
- TIP
    - 입력이 ‘1 2 3’과 같이 공백으로 구분되어 있는지, ‘123’처럼 연속된 문자형태인지 확인
    - 만약 문자열이 공백으로 구분되면 `split()`  메서드를 통해 분리해서 map 함수에 넣어야 함

### `zip` 함수

`zip(*iterables)` : 여러 개의 반복 가능한 데이터 구조를 묶어서 같은 위치에 있는 값들을 하나의 tuple로 만든 뒤 그것들을 모아 zip object로 반환하는 함수

- zip object: 짝지어진 결과를 하나씩 꺼내 쓸 수 있는 반복 가능한 객체 자료형
전체 값을 확인하려면 list나 tuple로 형변환을 해줘야 함

```python
# zip 함수 사용 기본
girls = ['jane', 'ashley']
boys = ['peter', 'jay']
pair = zip(girls, boys)

print(pair)  # <zip object at 0x000001C76DE58700>
print(list(pair))  # [('jane', 'peter'), ('ashley', 'jay')]
```

### `zip` 함수 활용

- 여러 개의 리스트를 동시에 조회할 때

```python
# zip 함수 활용
kr_scores = [10, 20, 30, 50]
math_scores = [20, 40, 50, 70]
en_scores = [40, 20, 30, 50]

for student_scores in zip(kr_scores, math_scores, en_scores):
    print(student_scores)

```

```python
# zip 함수 활용 (전치 행렬)
scores = [
    [10, 20, 30],
    [40, 50, 39],
    [20, 40, 50],
]

for score in zip(*scores):
    print(score)
```

- **TIP**
    - 반복 가능한 자료형의 길이가 다른 경우 가장 짧은 길이를 기준으로 묶어서 반환
    - 반드시 반복 가능한 자료형만 인자로 넣을 수 있음
    - zip object는 언패킹을 활용하여 변수에 바로 tuple 요소를 할당할 수 있음
