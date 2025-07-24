## `enumerate()`

### `enumerate()` 함수

`enumerate(iterable, start=0)` : iterable 객체의 각 요소에 대해 **인덱스와 값을 함께 반환**하는 내장함수

### `enumerate()` 활용

- `enumerate()` 의 index 정보를 이용해 넘버링으로 사용
    - start에 시작 값을 설정할 수 있음

```python
movies = ['인터스텔라', '기생충', '인사이드 아웃', '라라랜드']

for idx, title in enumerate(movies, start=1) :
    print(f'{idx}위: {title}')
```

```python
respondents = ['은지', '정우', '소민', '태호']
answer = ['', '좋아요', '', '괜찮아요']

for i, response in enumerate(answer) :
    if response == '' :
        print(f'{respondents[i]} 미제출')
```