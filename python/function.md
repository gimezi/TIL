# 함수

#### 함수를 사용하는 이유
 - 코드의 중복을 방지
 - 재사용성이 높아지고, 가독성과 유지보수성 향상

## 내장 함수(Built-in function)
: 파이썬이 기본적으로 제공하는 함수 \
(별도의 import 없이 바로 사용 가능)
#### 내장 함수 예시
- 절대값을 만드는 함수 abs
    ```python
    result = abs(-1)

    print(result) # 1으로 출력
    # 같이 쓰인 print도 내장 함수
    ```
- 리스트의 합을 구해주는 **sum**(list)
- 리스트를 순서대로 정렬해주는 list.sort()
- 내장 함수의 목록은 [Python 공식문서](https://docs.python.org/3/library/functions.html) 확인

## 함수의 구조
input -> (function) -> output

```python
def make_sum(pram1,pram2): # 매개변수
    """
    이것은 두 수를 받아서
    두 수의 합을 반환하는 함수입니다.

    >>> make_sum(1, 2)
    3
    """ 
    # 함수의 설명은 """를 붙여서 설명해줌
   
    return pram1 + pram2 #반환값
```

## 함수의 정의와 호출
- 함수 정의
  - 함수 정의는 **def** 키워드로 시작
  - def 이후 함수 이름 작성
  - 괄호안에 매개변수를 정의
- 함수 body
  - 콜론(:)다음에 들여쓰기가 된 코드 ㅡㄹ록
  - 함수가 실행 될 때 수행되는 코드를 정의
- 함수 반환 값
  - 필요한 경우, 결과를 반환할 수 있다 (출력이 없을 수도 있다.)
  - **return** 문은 함수의 실행을 종료하고, 결과를 반환
    ```python
    def greet(name):
        message = 'Hello' + name
        return message 
        # return이 없다면 결과값은 자동으로 None이 된다.
    
    result = greet('Alice')
    print(result)
    ```



# 매개변수와 인자
- 매개변수(parameter): 함수를 **정의**할 때, 함수가 받을 값을 나타내는 변수
- 인자(argument): 함수를 **호출**할 때, 실제로 전달되는 값
```python
def greet(name): # name은 매개변수
        message = 'Hello' + name
        return message 
    result = greet('Alice') #'Alice'는 인자
    print(result)
```

## 인자의 종류
- 위치 인자(Positional Arguments)
    - 함수 호출 시 인자의 위치에 따라 전달되는 인자
    - 위치인자는 함수 호출시 **반드시** 값을 전달해야 함!  
    ```python
    def greet(name,age):
        print(f'{name}님 {age}살이시군요')
    
    result = greet('Alice',25) # 인자가 두개 필요함
    ```
- 기본 인자(default Arguments)
  - 함수 정의에서 매개변수에 기본 값을 할당하는 것
  - 함수 호출 시 인자를 전달하지 않으면 기본값이 매개변수에 할당됨
  ```python
  def greet(name,age = 30): # 여기서 name을 default인자로 하면 오류가 남
      print(f'{name}님 {age}살이시군요') 
  # 기본인자는 뒤에서부터 써줘야합니다.
    
  greet('Alice') # age가 없어도 자동으로 30으로 출력이 됨
  ```
- 키워드 인자
  - 함수 호출 시 인자의 이름과 함께 값을 전달하는 인자
  - 매개변수와 인자를 일치시키지 않고, 특정 매개변수에 값을 할당할 수 있다
  - 인자의 순서는 중요하지 않으며, 인자의 이름을 명시하여 전달
  - 키워드 인자는 위치인자랑 같이 사용하지 못함
  ```python
  def greet(name,age = 30):
    print(f'{name}님 {age}살이시군요')
    
  greet('Alice', 25) 
  # Alice님 25살이시군요
  greet(25, 'Alice') 
  # 25님 Alice살이시군요
    
  #키워드 인자 이용
  greet(age = 25, name = 'Alice') 
  # Alice님 25살이시군요
  greet(age = 25, 'Alice')
  # 이렇게 한개만 해주는건 Error(위치인자와 키워드인자를 같이 사용했기때문) 
  ```
- 가변 인자 목록 
  - 정해지지 않은 개수의 인자를 처리하는 인자
  - 함수 정의 시 매개변수 앞에 '*'(에스터리스크)를 붙여 사용하며, 여러개의 인자를 tuple로 처리
  - 대표적인 예시: print()
  ```python
  def cal(*argm): # 이런식으로 매개변수에 *이 붙는다
      total = Sum(argm)
      print(f'합계는 {total}')
  ```  
- 임의의 키워드 인자 목록
  - 함수 정의시 매개변수 앞에 '**'를 붙여 사용하며, 여러 개의 인자를 dictionary로 묶어 처리  
  <dir>
- 함수 인자 권장 작성순서  
    : 위치 -> 기본 -> 가변 -> 키워드 -> 가변 키워드 (절대적인 것은 아니고 유연하게 조정 가능)

# 함수와 스코프
### Python의 범위(Scope)
- 함수는 코드 내부에 local scope를 생성하며, 그 외의 공간인 global scope로 구분
- scope
  - global scope: 코드 어디에서든 참조할 수 있는 공간
  - local scope: 함수가 만든 scope (함수 내부에서만 참조 가능)
    ```python
    def myfun():
        num = 1 # local scope

    print(num) # not defined 오류가 뜸
    ```
    - num은 local scope에 존재하기 때문에 global에서 사용 불가능
  
    ```python
    def myfun():
        num = 1 # local scope

    num = 3 # 위의 num과는 다른 것
    print(num) # 3
    ```
### 변수의 수명주기(lifecycle)
: 변수의 수명주기는 변수가 선언되는 위치와 스코프에 따라 결정
1. built-in scope: 파이썬이 실행된 이후부터 영원히 유지
2. global scope: 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지
3. local scope: 함수가 호출될 때 생성, 함수 종료까지만 유지

### 이름 검색 규칙
- 파이썬의 이름(식별자)는 각각 특정 공간에 저장되어 있음
- 다음과 같은 순서로 이름을 찾아감(LEGB rule)
  1. Local scope
  2. Enclosed scope
  3. Global scope
  4. Built-in scope
- 함수 내에서는 바깥 scope의 변수에 접근은 가능하나 수정은 할 수 없다.
- 예시
```python
print(sum([1, 2])) # 3 , 이 때의 sum은 built-in scope
sum = 10
print(sum) # 10
print(sum([1, 2])) # error: sum변수를 global에서 먼저 찾기 때문에
```
```python
a = 1
b = 2

def enclosed():
    a = 10
    c = 3

    def local(c):
        print(a, b, c) #10 2 500

    local(500)
    print(a, b, c) # 10 2 3

enclose()
print(a, b) #1 2
```

### 'global' 키워드
- 변수의 스코프를 전역 범위로 지정하기 위해 사용
- 일반적으로 함수 내에서 전역 변수를 수정하려는 경우에 사용
```python
num = 0 # 전역 변수

def incremet():
    global num # num을 전역 변수로 선언, 다 사용가능해짐
    num += 1

print(num) # 0
increment()
print(num) # 1
```
- *매개변수에는 global 사용불가능*

# 재귀 함수
- 특정 알고리즘 식을 표현할 때 변수 사용이 줄어들며, 코드의 가독성이 높아진다
- 1개 이상의 base case(종료되는 상황)가 존재하고, 수렴하도록 작성
- 예시: 팩토리얼
  ```python
  def factorial(n):
    if n == 0: # 종료 조건
        return 1
    return n * factorial(n - 1) 
    #재귀 호출: n과 n - 1의 팩토리얼을 곱한 결과를 반환
  ```
- 재귀함수는 
  1. 종료조건을 명확히
  2. 반복되는 호출이 종료조건으로 가도록(무한루프 안 돌도록)

# 유용한 내장 함수들
## map(function, iterable)
: 순회 가능한 데이터구조(iterable)의 모든 요소에 함수를 적용하고, 그 결과를 map object로 반환
- 가장 많이 쓰는 구조: map(int,input())이런식으로 제일 많이 쓰는데 function에 복잡한 함수도 가능, for문을 많이 줄일 수 있다
```python
import sys

sys.stdin = open('input.txt')

T = int(input())

a, b, c = map(int, input().split())

```

## zip(*iterables)
임의의 iterable을 모아 튜플을 원소로 하는 zip object를 반환

```python
sub = [1, 2, 3]
sta = ['역삼','강남','서울대']

print(dict(zip(sub, sta)))
# {1: '역삼', 2: '강남', 3: '서울대'}
print(list(zip(sub, sta)))
# [(1, '역삼'), (2, '강남'), (3, '서울대')]
```
```python
sub = [1, 2, 3, 4]
sta = ['역삼','강남','서울대'] #갯수가 서로 다르면 작은거 기준으로 나옴

print(list(zip(sub, sta)))
# [(1, '역삼'), (2, '강남'), (3, '서울대')]
```

## lambda
" lambda 매개변수: 표현식"
```python
addition = lambda x, y : x + y

print(additiont(3, 5)) #8
```
- map과 lambda를 같이 쓰기
```python
nums = [1, 2, 3, 4, 5]
result = map(lambda x: x*2, nums)
print(list(result))
```
- lambda는 일회용으로 쓰기 좋음
- 함수 이름이 필요가 없다
- return도 없다, 표현식의 결과가 바로 반환되므로!
- 어려우면 그냥 함수 정의해서 써도 됨

## Packing
여러 value를 하나의 sequence로 묶는 것
```python
# 패킹 예시
packing_value = 1, 2, 3, 4, 5
print(packing_value) # 튜플형태로 묶임

nums = [1, 2, 3, 4, 5]
a, *b, c = nums
print(a,b,c) # 1 [2, 3, 4] 5

# print를 이용한 패킹
print('hi', 'hello', 'goodbye', sep = '-') # hi-hello-goodbye
print('hi',end= '')
print('hello') #hihello

# *를 언패킹 연산자로 활용
names = ['minho', 'yong', 'chan']
print(*names) # minho yong chan

## ** 딕셔러니 언패킹 연산자
def my_f(x, y, z):
  print(x, y, z)
dic_value = {'x' : 1,'y' : 2,'z' : 3} #1 2 3
my_f(**dic_value)
```

# Module
- 라이브러리 = 모듈 + 패키지

```python
import math #control+우클릭 하면 더 자세하게 볼 수 있다

print(math.pi)
print(math.sqrt(4))

from random import *

print(randint(1,10))
```
- 직접 모듈 파일을 정의해서 사용가능

# 패키지

from my_package.math(파일 경로) import my_math(함수이름)

## 외부 패키지
- git 창에서 pip install request
```python
import requests

url = 'https://random-data-api.com/api/v2/users'

response = requests.get(url).json()
print(response)
# dic값이 결과로 나옴
```
위의 dic의 결과를 시각화해서 보여주는 [사이트](https://jsonviewer.stack.hu/)
