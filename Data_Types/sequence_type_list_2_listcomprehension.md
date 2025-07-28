## List Comprehension

### List Comprehension: 간결하고 효율적인 리스트 생성 방법

- TIP : “Pythonic”한 코드
    - 파이썬 개발자들이 선호하는 스타일로, 코드를 더 “파이썬답게” 작성하는 방법 중 하나

### List Comprehension 구조

`[표현식 for 변수 in 순회 가능한 객체 if 조건]` : if 조건 부분은 선택 사항

TIP : 각 구성 요소의 역할

- 표현식은 결과 리스트에 추가 값, 변수는 순회 중인 현재 요소, 순회 가능한 객체는 반복할 데이터, 조건식은 필터링 조건
- if 조건식 부분은 선택사항이며, 조건을 명시하지 않으면 모든 요소에 대해 표현식이 적용

사용 전/후 비교

```python
# 사용 전
numbers = [1, 2, 3, 4, 5]
squared_numbers = []

for num in numbers:
    squared_numbers.append(num**2)

print(squared_numbers)

# 사용 후
squared_numbers = [num**2 for num in numbers]
print(squared_numbers)
```

### List Comprehension 활용 예시

- 2차원 배열 생성 시 (인접행렬 생성)
    
    ```python
    # List Comprehension 활용 예시
    # "2차원 배열 생성 시 (인접행렬 생성 시)"
    data1 = [[0] * (5) for _ in range(5)]
    data2 = [[0 for _ in range(5)] for _ in range(5)]
    
    """
    [[0, 0, 0, 0, 0],
     [0, 0, 0, 0, 0],
     [0, 0, 0, 0, 0],
     [0, 0, 0, 0, 0],
     [0, 0, 0, 0, 0]]
    """
    ```
    

### List Comprehension의 가독성

가독성의 측면에서는 기본 for문 if문으로 구성하는 게 좋다.

→ Comprehension을 남용하지 말자 !

### 리스트를 생성하는 방법 비교

```python
# 리스트를 생성하는 방법 비교

# 1. for loop
result1 = []
for i in range(10):
    result1.append(i)

# 2. list comprehension
result2 = [i for i in range(10)]
# result2 = list(i for i in range(10))

# 3. map
result3 = list(map(lambda i: i, range(10)))

print(result1)
print(result2)
print(result3)

"""
성능 비교

1. list comprehension
    - 가장 'Pythonic'하고 **대부분의 경우 우수한 성능**을 보임
2. map
    - 특정 상황(int, str 등 **내장 함수와 함께 사용할 때**)에서 가장 빠름
    - 사용자가 직접 만든 함수나 **lambda와 함께 사용될 때는 list comprehension과 성능이 비슷하거나 약간 느릴 수 있음
3. for loop**
    - 일반적으로 가장 느리다고 알려져 있지만,
      python 버전이 올라가면서 다른 방식과 비슷하거나 **때로는 더 나은 결과를 보이기도 함**
    - 하지만, 여러 줄에 걸친 **복잡한 조건문**이나 **예외 처리 등이 필요할 때는 유일한 선택지**이며, 그 자체로 매우 유용함

결론
- **성능 차이는 대부분의 경우 마이크로초 단위로 미미**하므로, 
  코드의 가독성과 유지보수성을 최우선으로 고려하여 상황에 맞는 가장 명확한 방법을 선택하는 것을 권장
"""

```