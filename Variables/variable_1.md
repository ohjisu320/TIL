### 변수(variable)

- 값을 나중에 다시 이용하기 위해 그 값에 붙여주는 고유한 이름
- 할당?
    - 변수 할당 (Variable Assignment)
        - 표현식이 만들어 낸 값에 이름을 붙이는 과정
    - 할당문(Assignment statement)
        - `degrees = 36.5`
            - `degrees`: 변수 이름
            - `=` : 할당 연산자
            - `36.5` : 표현식
        - 변수명 규칙 **(시험에 나올듯)**
            - 영문 알파벳, 언더스코어(_), 숫자로 구성
            - 숫자로 시작할 수 없음
            - 대소문자를 구분
            
            ```python
            False      await      else       import     pass
            None       break      except     in         raise
            True       class      finally    is         return
            and        continue   for        lambda     try
            as         def        from       nonlocal   while
            assert     del        global     not        with
            async      elif       if         or         yield
            
            # keyword 모듈을 통해 확인 가능
            import keyword
            print(keyword.kwlist)
            ```
            
        - 변수, 값 그리고 메모리
            - 거리에 집 주소가 있듯이 **메모리(RAM 어딘가 …)**의 모든 위치에는 그 위치를 고유하게 식별하는 메모리 주소가 존재
                - 메모리 주소
                    - 각 사물함을 구별하기 위해 붙어있는 절대 겹치지 않는 고유한 사물함 번호
                    - 컴퓨터가 특정 데이터 값을 정확히 찾아가기 위해 사용하는 기계적인 숫자 주소
            - 객체(Object) ( 값 + 타입 + 주소 정보를 묶은 것 )
                - 고유한 ID ( 메모리 주소)
                - 제품의 바코드
                - 타입 (Type)
                    - 제품의 종류
                - 값(Value)
                    - 제품의 실제 내용물
            - 변수는 특정 객체를 가리키는(refer/point to) 이름표
                - 변수는 메모리 주소를 가지지(contain) 않습니다.
            - 그래서 변수란?
                - 값을 나중에 다시 사용하기 위해 그 값에 붙여주는 고유한 이름 **“객체를 가리키는 이름”**
            - **할당문** 동작 순서
                - `Variable = expression`
                    - 오른쪽 표현식 평가
                        - 가장 먼저 할당 연산자의 오른쪽에 있는 표현식 전체를 계산하여 하나의 결과값을 만듦
                    - 왼쪽 변수명 확인
                        - 이름이 처음 사용되었다면 새로운 이르표를 준비
                        - 이미 존재하는 이름이라면 기존 이름표를 그대로 사용
                    - 변수명과 결과값 연결
                        - 마지막으로 왼쪽의 변수명이 오른족에서 만들어진 결과값을 가리키도록 연결
                - 재할당
                    - 변수는 특정 값을 기억하거나 가리키는 이름
                    - 재할당은 이 변수가 가리키는 대상을 새로운 값으로 변경하는 행위
                        - `degrees = 'hello'`
                        - 재할당이 이루어지면, 변수는 이전 값을 완전히 잊고 새로운 값만 기억하게 됩니다.
                - 변수와 메모리 정리
                    
                    
                    | 용어 | 핵심 정의 | 비유 |
                    | --- | --- | --- |
                    | 객체 | 데이터의 실체 | ‘김철수’라는 사람 |
                    | 메모리 주소 | 객체가 저장된 고유한 위치 | 김철수의 실제 집 주소 |
                    | 변수 | 객체를 가리키는 이름표 | 주소록에 저장된 '철수’라는 이름 |


> 문장
>
    - 특정 동작을 지하는 실행 가능한 코드의 최소 단위
    - 표현식 vs 문장이 헷갈린다면?
        - 이 코드를 실행하면, 그래서 하나의 값이 남나요?
            - 표현식 → 네
                - 어떻게든 계산되거나 평가되어 하나의 값으로 귀결
                    - `10 +20` → 값 30이 남음
                    - `len("hello")` → 값 5가 남음
            
            - 문장 → 아니오
                - 컴퓨터에게 특정 동작을 ‘지시’하고 끝남 (값 자체가 남지 않음)
                - name = “홍길동” → 값을 변수에 할당하라는 지시

> **Style Guide**
> 
    - 변수명은 직관적인 이름 가져야 함
    - 공백 4칸을 사용하여 코드블록을 들여쓰기
    - 한 줄의 길이는 79자로 제한, 길어질 경우 줄 바꿈 사용
    - 문자와 밑줄(_)을 사용하여 함수, 변수, 속성의 이름을 작성
    - 함수 정의나 클래스 정의 등의 블록 사이에는 빈 줄을 추가
    - 이외 사항은 아래 링크 참고
        
> [PEP 8 – Style Guide for Python Code](https://peps.python.org/pep-0008/)
> 
> [PEP 20 – Style Guide for Python Code](https://icedhotchoco.tistory.com/entry/PEP-20)
