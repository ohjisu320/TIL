### 메서드(method): 객체에 속한 함수

- 프로그래밍에서 매서드(Method)는 객체(Object)가 특정 작업을 수행하도록 정의된 함수
    - 객체: 특정 데이터(정보)와그 데이터를 처리하는 기능(메서드)을 하나로 묶은 것
- 메서드는 **클래스(class) 내부**에 정의되는 함수
- 클래스는 파이썬에서 ‘타입을 표현하는 방법’이며 이미 은연 중에 사용해 왓음
- 예를 들어 help 함수를 통해 str을 호출해보면 class였다는 것을 확인 가능
    
    ```python
    print(help(str))
    """
    class str(object)
     |  str(object='') -> str
     |  str(bytes_or_buffer[, encoding[, errors]]) -> str
     |  
     |  Create a new string object from the given object. If encoding or
     |  errors is specified, then the object must expose a data buffer
     |  that will be decoded using the given encoding and error handler.
     |  Otherwise, returns the result of object.__str__() (if defined)
     |  or repr(object).
     |  encoding defaults to sys.getdefaultencoding().
     |  errors defaults to 'strict'.
     |
     |  Methods defined here:
     |
     |  __add__(self, value, /)
    -- More  --
    """
    ```
    

### 지금 시점에 알아야 할 것

- 메서드는 클래스에 속해 있는 함수이며, 각 데이터 타입 별로 다양한 기능을 가진 메서드가 존재

### 메서드 호출 방법

`'hello'.capitalize()` : 우리가 만든 `'hello'` 라는 객체(데이터)에게 원하는 명령(메서드)을 내리는 방법

- 일반적인 함수 호출 `function_name(args)` 과 다름

### 메서드 호출 예시

`데이터 타입 객체.메서드()` 

- 메서드 - 반환값이 있는 메서드, 없는 메서드가 나뉘어짐