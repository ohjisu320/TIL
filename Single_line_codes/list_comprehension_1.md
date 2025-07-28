## **리스트 컴프리헨션 (List Comprehension)**

리스트 컴프리헨션은 리스트를 생성하는 간결한 방법입니다.

`[표현식 for 항목 in 반복가능객체 if 조건]`과 같은 형태로 사용하며, 기존 리스트를 변환하거나, 특정 조건을 만족하는 새로운 리스트를 만들 때 유용합니다.

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = [x for x in numbers if x % 2 == 0]
print(even_numbers)  # 출력: [2, 4, 6, 8, 10]

squared_numbers = [x**2 for x in numbers]
print(squared_numbers) # 출력: [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```