# Input과 Print

## 가장 기본적인 input

```python 
char1 = input()
char2 = input("문자 한개를 입력하세요: ")
```

### 정수를 입력받는 방법
1. 한번에 바로
```python
num = int(input())
```
2. 받고 변환시키기
```python
num = input()
num = int(num)
```

### 공백 기준으로 받기(**split**)
```python
char1, char2 = input().split()
```

#### 정수의 경우 map함수를 이용해서 한번에 가능하다
```python
num1, num2 = map(int,input().split())
```
#### 공백뿐만 아니라 다른것들을 기준으로 가능하다
```python
year, month, day = map(int, input().split('.'))
```
#### 공백을 기준을 정수를 받고, 리스트에 바로 저장까지 시키기
```python
num_list = list(map(int,input().split()))
```

## Print 여러가지 방법
```python
name = input()
age = int(input())
height = float(input())
```
- 줄바꿈을 하고 싶지 않을 때 : end 이용
  ```python
  print(i, end = '')
  ```
1. 포멧코드
```python
print("저의 이름은 %s, 나이는 %d, 키는 %.2f" %(name, age, height))
# %s는 %d는 정수, %.2f는 소수점 두자리까지 반올림(없으면 6자리까지)
```
2. f-String (가장 넓게 사용가능)
```python
print(f"저의 이름은 {name}, 나이는 {age}, 키는 {height:.2f}")
```

3. .format()
```python
print("저의 이름은 {}, 나이는 {}, 키는 {}".format(name, age, height))
```
