# Data Structure(데이터 구조)

: 여러 데이터를 효과적으로 사용, 관리하기 위한 구조(str, list, dict등)
- 자료 구조라고도 함, 각 데이터의 효율적인 저장, 관리를 위해 구조를 나눠놓은 것
- 데이터 구조 활용: 문자열, 리스트, 딕셔너리 등 각 데이터 구조의 **메서드**를 호출하여 다양한 기능을 활용

[메서드](#메서드method)
- [시퀀스 메서드](#시퀀스-메서드)
  - [문자열(str)](#문자열str)
  - [리스트(list)](#리스트)
- [비시퀀드 메서드](#비시퀀트-메서드)
  - [세트(set)](#set)
  - [딕셔너리(dict)](#딕셔너리dict)

# 메서드(Method)
: 객체에 **속한** 함수 (객체의 상태를 조작하거나 동작을 수행)

- 메서드 특징
  - 메서드는 **클래스** 내부에 정의되는 함수
  - 클래스: 파이썬에서 '타입을 표현하는 방법'
  - ex) help 함수를 이용해 str을 호출해보면  class임을 알 수 있다.
  ```python
  print(help(str))
  """
    class str(object)
    |  str(object='') -> str
    |  str(bytes_or_buffer[, encoding[, errors]]) -> str
    |  
    |  Create a new string object from the given object.
  """
  ```
- 메서드는 어딘가(클래스)에 속해 있는 함수이며, 각 데이터 타입별로 다양한 기능을 가진 메서드가 존재
- 메서드 호출 방법  
    ***데이터 타입 객체.메서드()***
  ```python
  # 문자열 메서드
  print('hello'.captitalize()) #Hello

  # 리스트 메서드
  nums = [1, 2, 3]
  nums.append(4)

  print(nums) # [1, 2, 3, 4]
  ```

## 시퀀스 메서드
: sequence types(여러 개의 값들을 순서대로 나열하여 저장하는 자료형 / str, list, tuple, range등)
### 문자열(str)
#### "문자열" *조회/탐색* 및 검증 메서드

- `.find(x)`: x의 첫번째 위치를 반환/ 없다면, **-1**
  ```python
  print('banana'.find('a')) # 1
  print('banana'.find('z')) # -1 없으니까
  ```

- `.index(x)`: x의 첫번째 위치를 반환/ 없다면, **오류발생**
  ```python
  print('banana'.find('a')) # 1
  print('banana'.find('z')) # ValueError
  ```
  
- .`isupper(x)` / `.islower(x)`: 문자열이 모두 대문자/ 소문자로 이루어져 있는지 **확인**

- `.isalpha(x)`: 문자열이 알파벳으로만 이루어져 있는지 확인
  ```python
  string1 = 'Hello'
  string2 = '123'

  print(string1.isalpha()) # True
  print(string2.isalpha()) # False
  ```

- `.istitle(x)`: 타이틀 형식 여부
- 다른 메서드들은 [링크](https://docs.python.org/ko/3.9/library/stdtypes.html#text-sequence-type-str)참조

#### 문자열 *조작* 메서드

- `.replace(old, new[,count])`: 바꿀 대상 글자를 새로운 글자로 바꿔서 반환, 여기서 [대괄호]는 선택 인자 (EBNF 표기법 참조)
  ```python
  text = 'Hello World'
  new_text = text.replace('world', 'Python')
  print(new_text) # Hello Python
  ```
- `.strip([chars])`: 문자열의 시작과 끝에 있는 공백, 또는 지정한 문자를 제거
    ```python
    text = '       Hello world        '
    new_text = text.strip()
    print(new_text) # 'Hello world'
    ```
- `.split(sep = none, maxsplit = -1)`: 지정한 문자를 구분자로 문자열을 분리하여 문자열의 리스트로 반환
  ```python
  text = 'hello, world'
  words = text.split(',')
  print(words) # ['hello', 'world']
  ```
- 'separator'`.join([iterable])`: iterable 요소들을 원래의 문자열을 구분자로 이용하여 하나의 문자열로 연결
  ```python
  words = ['hello', 'world']
  text = '-'.join(words)
  print(text) # 'hello-world'
  ```
- `.capitalize()`: 문자열의 첫글자는 대문자, 나머지는 소문자로 변환
- `.title()`: 띄어쓰기 기준으로 각 단어의 첫글자는 대문자, 나머지는 소문자로 변환
- `.upper()` / `.lower()`: 문자열의 모든 문자를 대문자 / 소문자로 변환
- `.swapcase()`: 대소문자 상호전환, 대문자는 소문자로, 소문자는 대문자로 전환
  ```python
  text = 'heLLo woRLd'

  print(text.capitalize()) # 'Hello world'
  print(text.title()) # 'Hello World'
  print(text.upper()) # 'HELLO WORLD'
  print(text.lower()) # 'hello world'
  print(text.swapcase()) # 'HEllO WOrlD'
  ```

- **메서드는 이어서 사용 가능!**

### 리스트
#### 리스트 값 *추가 / 삭제* 메서드
- `.append(x)`: 리스트 마지막에 항목 x를 추가
  ```python
  a = [1, 2, 3]
  a.append(4)
  print(a) #[1, 2, 3, 4] 뒤에 추가 됨
  ```
- `.extend(iterable)`: 리스트에 다른 반복 가능한 객체의 모든 항목을 추가
  ```python
  a = [1, 2, 3]
  a.extend([4, 5])
  print(a) # [1, 2, 3, 4, 5]
  ```
- `.insert(i, x)`: 리스트 i번째 위치에 x를 삽입
  ```python
  a = [1, 2, 3]
  a.insert(1, 5)
  print(a) # [1, 5, 2, 3]
  ```
- `.remove(x)`: 리스트에서 첫번째로 나오는 x 삭제
  ```python
  a = [1, 2, 3, 2, 5, 2]
  a.remove(2)
  print(a) # [1, 3, 2, 5, 2]
  ```
- `.pop(i)`: 인덱스가 i인 항목을 제거하고 ***반환***, 작성하지 않을 경우 마지막 항목이 제거됨
  ```python
  a = [1, 2, 3, 4, 5]

  item = a.pop(2)

  print(item) # 3
  print(a) # [1, 2, 4, 5]
  ```
- `.clear()`: 리스트의 모든 항목을 삭제
  ```python
  a = [1, 2, 3]
  a.clear()
  print(a) # []
  ```

#### 리스트 *탐색 / 정렬* 메서드
- `.index(x)`: 리스트에서 첫번째로 일치하는 항목의 인덱스를 반환
  ```python
  a = [1, 2, 3]
  index = a.index(2)
  print(index) # 1
  ```
- `.count(x)`: 리스트에서 항목 x가 등장하는 횟수를 반환
  ```python
  a = [1, 2, 2, 3, 3, 2]
  print(a.count(2)) # 3
  print(a.count(6)) # 0
  ```
- `.sort()`: 원본 리스트를 오름차순으로 정렬(원본을 변환시킴)
  ```python
  a = [2, 3, 1]
  a.sort()
  print(a) # [1, 2, 3]

  # 내림차순으로도 가능
  a.sort(reverse = True)
  print(a) # [3, 2, 1]
  ```

- `.reverse()`: 리스트의 순서를 역순으로 변경(정렬이 아니라 그냥 뒤집어줌)
  ```python
  a = [2, 3, 4, 3]
  a.reverse()
  print(a) # [3, 4, 3, 2]
  ```

#### (참고) 문자열에 포함된 문자들의 유형을 판별하는 메서드
- `isdecimal()`: 문자열이 모두 숫자로 이루어져 있어야 'True'
- `isdigit()`: 유니코드 숫자도 인식('①'도 숫자로 인식)
- `isnumeric()`: 더 넓은 범위의 유니코드 문자도 인식(분수, 지수, 루트 기호도 숫자로 인식)

## 비시퀀트 메서드
### 세트(set)
- `.add(x)`: 세트에 x를 추가
- `.clear()`: 세트의 모든 항목을 제거
  ```python
  my_set = {1, 2, 3}
  my_set.clear()
  print(my_set) # set() , 비어있는 세트는 ()를 사용함
  ```

- `.remove(x)`: 세트에서 항목 x를 제거, 없을 경우 **에러**가 발생
  ```python
  myset= {1, 2, 3}
  myset.remove(2)
  print(myset) # {1, 3}

  myset.remove(10)
  print(myset) # error
  ```
- `.discard(x)`: 세트에서 항목 x를 제거, 없을 경우 **None** 출력
  ```python
  myset= {1, 2, 3}
  myset.discard(2)
  print(myset) # {1, 3}

  myset.discard(10)
  print(myset) # {1, 2, 3}
  ```
- `.pop()`: 세트에서 **임의**의 요소를 제거하고 반환(set는 순서가 없기 때문에)
  ```python
  myset = {1, 2, 3}
  element = myset.pop()

  print(element) # 1
  print(myset) # {2, 3}
  # 세트의 요소가 정수일때는 계속 같은 값이 나옴(해쉬값 고정)
  # 왜냐면 pop이 해쉬값에서 제일 앞에 있는 값이 반환되기 때문에
  # 세트의 요소가 문자열 등일 때는 랜덤 값이 나옴(매번 해쉬값이 바뀜)
  ```
- `.update(iterable)`: 세트에 다른 iterable 요소를 추가(≒extend)


#### 세트의 집합 메서드
- `set1.difference(set2)` = 차집합 (set1 - set2)
- `set1.intersection(set2)` = 교집합(set1 & set2)
- `set1.union(set2)` = 합집합 (set1 | set2)
- `set1.issubset(set2)` = 부분집합인지? (True / False 반환) set1 ⊂ set2
- `set1.issuperset(set2)` = 부분집합인지? (True / False 반환) set1 ⊃ set2

### 딕셔너리(dict)
: 고유한 항목들의 정렬되지 않은 컬렉션

- `.get(key[,default])`: 키 연결된 값을 반환하거나 키가 없으면 None 혹은 기본 값을 반환
  ```python
  person = {'name' : 'Mino', 'age' : 25}
  person.get('name') # Mino
  person.get('country') # None
  person.get('country','Korea') # Korea

  # person(['name']) # Mino
  # preson(['country']) # 얘는 에러가 뜸
  ```
- `.keys()`: 딕셔너리 키를 모은 객체를 반환(키만 반환 해줌)
  ```python
  person = {'name' : 'Mino', 'age' : 25}
  person.keys() # dict_keys(['name','age']), 리스트형태로 출력

  for k in person.keys():
    print(k) # name \n age
  ```
- `.values()`: 딕셔너리 값을 모음 객체를 반환
  ```python
  person = {'name' : 'Mino', 'age' : 25}
  person.values() # dict_keys(['name','age']), 리스트형태로 출력

  for i in person.valuses():
    print(i)
  ```
- `.items()`: 딕셔너리 키/값 쌍을 모은 객체를 반환
  ```python
  person = {'name' : 'Mino', 'age' : 25}
  for k, v in person.items():
    print(k, v)
  ```
- `.pop(key[,default])`: 키를 제거하고 연결됬던 값을 반환, 없으면 에러나 dafault
  ```python
  person = {'name' : 'Mino', 'age' : 25}

  print(person.pop('age')) #25
  print(person) # {'name' : 'Mino'}  age가 없어진걸 확인할 수 있다.
  print(person.pop('country')) # KeyError
  print(person.pop('country', None)) # None
  ```
- `.setdefault(key[,default])`: 키와 연결된 값을 반환, 주어진 값을 추가하고 default를 반환
    ```python
    person = {'name' : 'Mino', 'age' : 25}

    print(person.setdefault('country','Korea')) # Korea
    print(person) # {'name' : 'Mino', 'age' : 25 ,'country' : 'Korea'}
    ```
- `.update([other])`: other가 제공하는 키/값 쌍으로 딕셔너리를 갱신, 기존 키가 있다면 덮어쓴다
  ```python
  person = {'name' : 'Mino', 'age' : 25}
  other_person = {'name' : 'Felix', 'gender' : 'Male'}

  person.update(other_person)
  print(person) # {'name' : 'Felix', 'age' : 25, 'gender' : 'Male'} 이름은 덮어씀

  person.update(age = 23)
  print(person) # {'name' : 'Felix', 'age' : 23, 'gender' : 'Male'}

  person.update(country = 'Australia')
  print(person) # {'name' : 'Felix', 'age' : 23, 'gender' : 'Male', 'country' : 'Australia'}
  ```
#### 딕셔너리 메서드를 이용해서 할 수 있는 예제
- 여러가지 blood type이 있을 때, 각 혈액형당 몇명인지 dict형태로 정리하기
  ```python

  blood_types = ['a', 'b', 'b', 'ab', 'o', 'a', 'b', 'b', 'ab', 'o']


  # 1. get 안쓰고 하기
  new_dict = {}
  for blood_type in blood_types:
      if blood_type in new_dict:
          new_dict[blood_type] += 1
      else:
          new_dict[blood_type] = 1
          # 없다면 = 처음 설정되는 키
  print(new_dict) # {'a': 2, 'b': 4, 'ab': 2, 'o': 2}


  # 2. get 쓰고 하기
  new_dict = {}
  for blood_type in blood_types:

      new_dict[blood_type] = new_dict.get(blood_type, 0) + 1
      # 기존의 값이 있을 때, 앞에 어짜피 안되니까
  print(new_dict) # {'a': 2, 'b': 4, 'ab': 2, 'o': 2}


  # 3. setdefault 이용
  new_dict = {}
  for blood_type in blood_types:
      new_dict.setdefault(blood_type, 0)
      new_dict[blood_type] += 1
  print(new_dict) # {'a': 2, 'b': 4, 'ab': 2, 'o': 2}

  # 4. counter 이용
  from collections import Counter
  print(Counter(blood_types)) # Counter({'b': 4, 'a': 2, 'ab': 2, 'o': 2})
  ```