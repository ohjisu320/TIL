## 조건문(Conditional Statement)

### 조건문의 정의

- 주어진 조건식을 평가하여 해당 조건이 참(True)인 경우에만 코드 블록을 실행하거나 건너뜀

## `if` statement

### 조건문의 기본 구조

- `if`문
    - 조건문의 기본 형태
    - if문에 작성된 조건을 만족할 대 내부 코드 실행
    - 작성되는 조건은 ***표현식**으로 작성
        - 표현식: 결과가 값으로 평가되는 코드
- `elif` 문
    - 이전의 조건을 만족하지 못하고 추가로 다른 조건일 필요할 때 사용
    - 여러 개의 elif 문을 사용할 수 있음
- `else` 문
    - 모든 조건들을 만족하지 않으면 실행됨

### 복수 조건문

- 조건식을 동시에 검사하는 것이 아니라 “순차적”으로 비교
- 조건식의 순서에 따라 원하는 결과가 나오지 않을 수 있음을 주의

```bash
# 복수 조건문
## 순서 1. 결과: 매우 나쁨
dust = 155

if dust > 150:
    print('매우 나쁨')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')

## 순서 2. # 결과: 보통
dust = 155

if dust > 30:
    print('보통')
elif dust > 80:
    print('나쁨')
elif dust > 150:
    print('매우 나쁨')
else:
    print('좋음')

```

### 중첩 조건문

- 조건문 (if) 내부에 다른 조건문 (if)작성 가능

```python
# 중첩 조건문 동작 예시
# 출력: 매우 나쁨
#      위험해요! 나가지 마세요!
dust = 480

if dust > 150:
    print('매우 나쁨')
    if dust > 300:
        print('위험해요! 나가지 마세요!')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')

```