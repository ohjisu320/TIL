## 내장 함수 (Built-in function)

### 개념

- 파이썬이 기본적으로 제공하는 함수(별도의 `import` 없이 바로 사용 가능)
- 내장 함수는 편리하지만, 이름이 같아도 다른 언어에서는 다르게 동작할 수 있기에 주의해야 함.
- 단순히 함수를 사용하는 것에 그치지 않고, **내부 동작 원리를 이해**하면 문제 해결에 더 효과적으로 활용하고 **성능 저하 같은 잠재적 문제를 피할 수 있음**
- 이는 더 나은 코드를 작성하는 개발자의 기본기입니다.

### 자주 사용되는 내장 함수 예

```python
numbers = [1, 2, 3, 4, 5]

print(numbers)  # [1, 2, 3, 4, 5]
print(len(numbers))  # 5
print(max(numbers))  # 5
print(min(numbers))  # 1
print(sum(numbers))  # 15
print(sorted(numbers, reverse=True))  # [5, 4, 3, 2, 1]

```