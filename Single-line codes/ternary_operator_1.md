## **삼항 연산자 (Ternary Operator)**

삼항 연산자는 조건에 따라 다른 값을 반환하는 간결한 표현식입니다.

`값1 if 조건 else 값2` 와 같이 사용하며, `if/else`문을 한 줄로 표현할 수 있습니다.

```python
age = 20
status = "성인" if age >= 18 else "미성년자"
print(status)  # 출력: 성인

number = 7
result = "짝수" if number % 2 == 0 else "홀수"
print(result) # 출력: 홀수
```