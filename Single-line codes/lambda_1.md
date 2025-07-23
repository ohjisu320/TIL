## **람다 함수 (Lambda Function)**

람다 함수는 이름 없이 정의되는 익명 함수입니다. 주로 간단한 연산을  간단하게 표현할 때 유용하며,

`lambda 인자: 표현식` 형태로 작성합니다. 

예를 들어, 두 수를 더하는 람다 함수는 `lambda x, y: x + y`와 같이 표현할 수 있습니다.
```python
add_numbers = lambda x, y: x + yprint(add_numbers(5, 3))  # 출력: 8
```