## Trailing Comma

- 컬렉션의 마지막 요소 뒤에 붙는 쉼표
- 일반적으로 Trailing Comma 작성은 ‘선택사항’
- 단 하나의 요소로 구성된 튜플을 만들 때는 필수

- Trailing Comma 좋은 예시
    
    ```python
    # Good
    
    item = [
    		'item1',
    		'item2',
    ]
    
    my_func(
    		'value1',
    		'value2',
    )
    ```
    
- Trailing Comma 나쁜 예시
    
    ```python
    # Bad
    
    items = ['item1', 'item2',]
    my_func('value1', 'value2',)
    
    # 한 줄 작성 시에는 불필요
    items = ['item1', 'item2']
    my_func('value1', 'value2')
    ```
    