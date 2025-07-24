## 패키지

### 패키지의 정의

- 연관된 모듈들을 하나의 디렉토리에 모아 놓은 것
- 누군가가 잘 만들어 둔 코드 꾸러미
- 패키지 안에 패키지가 들어갈 수도 있고, 모듈이 들어갈 수도 있음
    - folder 안에 folder, folder 안에 file
- 어디까지 from 으로 불러올 지는 `.` 으로 결정
    
    ```python
    ## 사용자 정의 패키지
    from my_package.math import my_math 
    from my_package.statistics import tools
    
    print(my_math.add(1, 2))
    print(tools.mod(1, 2))
    
    ```

### TIP

- 너무 많은 기능이 한 파일에 몰려 있으면 사용자가 헷갈릴 수 있음
- 비슷한 기능은 묶고, 관련 없는 것은 나누는 것이 사용하기 편함
- 폴더/파일 명은 소문자 + 언더스코어(_)를 쓰는 게 깔끔하고 표준적

### 패키지의 종류

- PSL (Python Standard Library) 내부 패키지
    - 파이썬을 설치하면 자동으로 사용할 수 있는 기본 패키지
    - 다양한 기능이 들어 있어 복잡한 작업도 쉽게 처리할 수 있음
    - `math`, `os`, `sys` , `random` 등 다양한 패키지가 존재
    - 설치 없이 바로 `import` 해서 사용 가능
- 파이썬 외부 패키지
    - 필요한 기능을 사ㅛ용하기 위해 직접 설치해서 쓰는 패키지
    - 다양한 패키지들이 존재
    - 사용할 패키지를 설치할 때는 `$ pip` 를 사용

### `pip`란?

- 외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템
    - 직접 만든 패키지도 이곳에 등록해서 배포 가능

### 패키지 설치

- 최신 버전 / 특정 버전  / 최소 버전을 명시하여 설치할 수 있음

```bash
$ pip install SomePackage 
$ pip install SomePackage==1.0.5
$ pip install SomePackage>=1.0.4
```

- TIP
    - 다양한 패키지 버전이 존재하기 때문에 개발시 호환성 이슈가 생기지 않는 지 확인이 필요합니다.
    - 설치한 패키지는 `pip freeze > requirements.txt 명령어로 버전 정보를 기록해 두는 것이 좋음
    - requirements/.txt 파일은 협업 시 개발 환경을 통일하는 데 큰 도움이 됨

### requests 외부 패키지 설치 및 사용 예시

- requests 패키지
    - 파이썬에서 웹에 요청을 보내고 응답을 받는 걸 아주 쉽게 만들어 주는 외부 패키지
    - pip를 통해 requests 패키지를 설치
        
        ```bash
        $ pip install requests 
        ```
        
    - requests를 import 하여 웹에 데이터 요청
        
        ```bash
        import requests
        
        # 공휴일 정보 API
        url = "https://date.nager.at/api/v3/publicholidays/2025/KR"
        response = requests.get(url).json()
        
        # 파이썬 객체로 변환된 공휴일 정보를 화면에 출력합니다.
        print(response)
        
        ```
        
    - `.get(url)`
        - 주어진 url로 요청하는 requests 패키지 메서드
    - `.json()`
        - 문자열로 이루어진 json 자료형을 dict 자료형으로 변환시키는 requests 패키지 메서드
            - 메서드는 OOP에서 진행
    
    ### 패키지의 사용 목적
    
    - 모듈들의 이름공간을 구분하여 충돌을 방지
    - 모듈들을 효율적으로 관리하고 할 수 있도록 돕는 역할