## 세트

### Set: 고유한 항목(중복 X)들의 정렬되지 않은 컬렉션(=비시퀀스)

- Set은 내부적으로 **해시 테이블**을 사용하여 데이터를 저장합니다.
- 이로 인해 항목의 **고유성**을 효율적으로 보장하며, 항목의 **추가, 삭제, 존재 여부 확인( in 연산)**이 데이터의 크기에 관계없이 **매우 빠름**
- 또한, 합집합(Union), 교집합(Intersection), 차집합(Difference) 등 **수학적인 집합 연산**을 간편하게 수행할 수 있는 것이 가장 큰 특징
    - `list → set → list` 로 중복 제거할 때 주의사항:
    순서가 그대로 혹은 보장하라는 요구사항이 있었다면 **틀림**! **순서**가 ****뒤바뀔 수 있음

### 세트의 메서드

| 메서드 | 설명 |
| --- | --- |
| **`s.add(x)`**  | **세트 s에 항목 x를 추가. 이미 x가 있다면 변화 없음
순서가 존재하지 않아서 반환 값이 계속 재정렬됨** |
| `s.update(iterable)`  | 세트 s에 다른  **iterable** 요소를 추가 |
| `s.clear()`  | 세트 s의 모든 항목을 제거.
출력 값은 `set()`  |
| **`s.remove(x)`**   | **세트 s에서 항목 x를 제거. 항목 x가 없을 경우 Key error
반환 값은 따로 없음** |
| `s.pop()`  | 세트 s에서 임의의 항목을 반환하고, 해당 항목을 제거 |
| `s.discard()`  | 세트 s에서 항목 x를 제거
- remove와 달리 에러 없음  |

### 세트의 집합 메서드

```python
set1 = {0, 1, 2, 3, 4}
set2 = {1, 3, 5, 7, 9}
set3 = {0, 1}

print(set1.difference(set2)) # {0, 2, 4} - 
print(set1.intersection(set2)) # {1, 3} &
print(set1.issubset(set2)) # False <=
print(set3.issubset(set1)) # True <=
print(set1.issuperset(set2)) # False >=
print(set1.union(set2)) # {0, 1, 2, 3, 4, 5, 7, 9} |

```