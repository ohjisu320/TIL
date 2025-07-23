[[Python] 파이썬 f-스트링 활용법 2탄: 고급 기능과 팁 💡](https://datasciencebeehive.tistory.com/138)

<aside>
💡f-string은 HTML에 jinja를 먹였을 때와 비슷하게 작동한다.


> HTML + jinja에서는 정해진 구간 안에서 외부 변수, for문, if문 등 다양하게 쓰인다.
> f-string 또한 그 쓰임새와 비슷하다. 
> 다만 다른 점이 두 가지 있다.
> 
> 첫번째는 환경이다. jinja는 당연히 HTML-python의 웹 환경에서 동작한다.
> 따라서 HTML 파일 내에 JINJA가 import되어 있어야만 동작한다.
> 반면 f-string은 당연히 python에 내장되어 있는 기능이기에 따로 import가 필요 없다.
> 
> 두번째는 구현 방법이다.
> f-string의 경우 {} 안에서만 작동하기 때문에 **for문이나 if문을 구현할 경우 한줄 코딩으로 구현**해야 한다.
> 
> - **조건부 표현식 사용 (Conditional Expressions in f-Strings)**
> - **함수 호출 및 메서드 체이닝 (Function Calls and Method Chaning)**
> - **중첩 f-string  (Nested f-string)**
> - **딕셔너리 데이터 포매팅 (Formatting Dictionary Data)**
> - **다양한 진법 변환 (Advanced Base Conversions)**
> - **로컬 변수 참조 (Referencing Local Variables)**
> - **큰 따옴표와 작은 따옴표 혼용 (Mixing Single and Double Quotes)**
> - **복잡한 데이터 구조 포매팅 (Formatting Complex Data Structures)**
</aside>

1. **조건부 표현식 사용**
    - f-string 내에서 조건부 표현식을 사용할 수 있음
    - 이를 통해 문자열에 포함될 값을 조건에 따라 동적으로 설정 가능함
    - 다만, {} 안에서만 작동하기 때문에 한줄 코딩만 가능하다.
        - if 문의 경우 삼항 조건 연산자 (`A if condition else B`)에서만 가능
    
    ```python
    score = 85
    print(f'합격 여부: {"합격" if score >= 60 else "불합격"}')
    # 합격 여부: 합격
    ```
    
2. **함수 호출 및 메서드 체이닝 (Function Calls and Method Chaning)**
    - f-string 안에서 함수나 메서드를 호출해서 따로 `variable = function()` 와 같은 변수 할당 없이 간편하게 문자열 처리가 가능
    
    ```python
    name = "laila"
    print(f'{name.capitalize()}님, 환영합니다!')
    # Laila님, 환영합니다! 
    ```
    
3. **중첩 f-string (Nested f-string)**
    - f-string 안에 또 다른 f-string을 넣을 수 있음
    - 이 기능은 복잡한 문자열 formatting이 필요한 경우에 매우 유용함
    - `f"{f'...'}"`는 **표현식을 분리하거나, 중간 결과를 한 번 더 포맷해야 할 때만 유용**함.
    
    ```python
    name = "로이"
    greeting = "안녕하세요"
    message = f"{f'{greeting}, {name}!'} 오늘도 좋은 하루 보내세요!"
    print(message)
    # 안녕하세요, 로이! 오늘도 좋은 하루 보내세요!
    ```
    
    - ✅ 중첩 f-string이 실제로 유용한 예시들
        
        **포맷된 문자열을 동적으로 만들어야 할 때**
        
        > ✅ `f'{currency}{price_str}'` 내부 포맷이 외부 메시지에 들어감 → 재사용성, 분기 포맷에 유리
        ➡ `price_str`  을 따로 뽑아 다른 곳에서도 재사용하거나, 외부에서 조합할 수 있게 하기 위해 중첩 사용
        > 
        
        ```python
        price = 12000
        currency = "₩"
        format_type = "comma"  # 또는 "plain"
        
        price_str = f"{price:,}" if format_type == "comma" else str(price)
        message = f"총 금액은 {f'{currency}{price_str}'}입니다."
        print(message)
        # 총 금액은 ₩12,000입니다.
        ```
        
4. **딕셔너리 데이터 포매팅(Formatting Dictionary Data)**
    - 딕셔너리의 키를 직접 참조해서 값을 f-string으로 출력 가능
    
    ```python
    person = {'name': '로이', 'age': 28}
    print(f'이름: {person["name"]}, 나이: {person["age"]}')
    # 이름: 로이, 나이: 28
    ```
    
5. **다양한 진법 변환 (Advanced Base Conversions)**
    - 10진수를 다양한 진법으로 변환하기도 가능
    - 2진수로 변환 `:#b`
    - 8진수로 변환 `:#o`
    - 16진수로 변환 `:#x`
    
    ```python
    number = 255
    print(f'10진수: {number}, 2진수: {number:#b}, 16진수: {number:#x}, 8진수: {number:#o}')
    # 10진수: 255, 2진수: 0b11111111, 16진수: 0xff, 8진수: 0o377
    ```
    
6. **로컬 변수 참조 (Referencing Local Variables)**
    - f-string 내에서 locals()를 사용하면 현재의 모든 로컬 변수를 참조할 수 있음
    - 이때 로컬변수는 locals()라는 내장 함수(built-in function) 내에 딕셔너리 값으로
    들어가 있기 때문에 key:value값으로 접근 `locals()[ “value_name” ] = value`
    
    ```python
    item = "사과"
    quantity = 5
    print(f'아이템: {locals()["item"]}, 수량: {locals()["quantity"]}')
    # 아이템: 사과, 수량: 5
    ```
    
7. **큰 따옴표와 작은 따옴표 혼용 (Mixing Single and Double Quotes)**
    - f-string에서 문자열 내 큰 따옴표와 작은 따옴표를 혼용하여 보다 유연하게 사용 가능
    
    ```python
    quote = "Life is what happens when you're busy making other plans."
    print(f'명언: "{quote}"')
    # 명언: "Life is what happens when you're busy making other plans."
    ```
    
8. **복잡한 데이터 구조 포매팅 (Formatting Complex Data Structures)**
    - 리스트나 튜플 같은 복잡한 데이터 구조도 **for문**을 사용하여  f-string으로 간단하게 포맷 가능
    - 다만 **for문**의 경우 `[...] for item in data` → **리스트 컴프리헨션으로만 구현 가능**
    
    ```python
    data = [("사과", 5), ("바나나", 3), ("포도", 10)]
    print(f'장바구니: {", ".join([f"{item[0]} {item[1]}개" for item in data])}')
    # 장바구니: 사과 5개, 바나나 3개, 포도 10개
    ```