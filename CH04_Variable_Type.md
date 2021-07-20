Python CH.04 실습

### 4.1 변수

> Data를 저장하는 곳(상자)를 변수(Variable)라 하고, 이에 붙이는 이름을 변수명(변수 이름)이라 함

- 변수 선언

  - `변수명 = data` 으로 값을 변수에 저장하는 것을 **변수를 선언**한다고 표현

    - data는 숫자, 문자열 등 원하는 값을 넣어주면됨 (파이썬에서는 data에 따라 변수의 type을 결정해줌)
    - 여러개의 변수를 한 번에 선언할 경우는 `,`, `[ ]`를 이용

    ```python
    a = 10				# a라는 변수에 10(int)이라는 값을 저장(변수 선언)
    
    a, b = 10, 20 		# 순서대로 a에는 10, b에는 20이 저장됨
    
    [a, b] = [10, 20]	# 순서대로 a에는 10, b에는 20이 저장됨
    
    a = b = 10			# a와 b에 10이라는 같은 값을 저장함
    
    a = None			# a라는 변수는 값이 저장되어있지 않음(비어있음)
    ```

  - 선언하면 변수는 컴퓨터의 메모리에 저장됨

  - 변수명 규칙

    - 변수명은 문자, 숫자, 밑줄기호`_`를 이용해서 생성(보통 `_`로 시작하진 않음)
    - 숫자로 시작할 수 없음
    - 대소문자를 구분함
    - 공백을 포함할 수 없음
    - `_`이외의 기호(%,$,#,^,! 등)는 사용할 수 없음
    - 예약어(None, True, False, as, and, break, class, continue, def, elif, if, import 등)는 사용할 수 없음

- 변수 활용

  - `print(변수명)`으로 직접 값을 넣지 않아도 변수에 저장되어있는 값을 출력
  - 변수에 저장된 값이 **수**일경우(int, float 등) 연산도 가능

  ```python
  a = 10
  b = 20
  c = a+b			# 변수 a,b가 정수형변수이기 때문에 사칙연산이 가능
  d = a			# 변수 선언시 기존의 변수로도 대입이 가능(a의 값을 d에 저장)
  
  print(a)
  print(b-5)		# print()에 직접 변수를 넣을 수 있고, 사칙연산식을 넣을 수 있음(결과값 출력)
  print(c)		
  print(d)
  
   - 10
   - 15
   - 30
   - 10
  ```



### 4.2 문자열

> 문자열은 문자들의 나열을 의미 type은 **str** 
>
> 작은따옴표(`' '`), 큰따옴표(`" "`), 삼중작은따옴표(`'''`), 삼중큰따옴표(`"""`)로 묶어서 표현

```python
a = 'hello'								# ' '로 묶어서 문자열 표현
b = "world"								# " "로 묶어서 문자열 표현 (단, ', " 섞어서 사용 불가능)
c = "hello 'hi' hola"					# 문자열 내 따옴표를 사용하고 싶을 때는 
										# 큰따옴표 안에 작음따옴표를, 작음따옴표 안에 큰따옴표를
										# 사용할 수 있음
d = '''this is used to express
several sentences.'''					# 여러 문장을(줄바꿈 포함) 표현하고 싶을때나
e = """use when you want to include
both 'single' and "double" quotes """	# ' ', " "을 문장내에서 모두 사용하고 싶을 때는 
										# 삼중따옴표를 사용하면 된다. 
f = '문자열 안에 \'따옴표\'를 넣고 싶을때는 따옴표앞에 \(backslash)를 붙이면 된다.'
										  
- hello
- world
- hello 'hi' hola
- this is used to express
  several sentences.
- use when you want to include
  both 'single' and "double" quotes 
- 문자열 안에 '따옴표'를 넣고 싶을때는 따옴표앞에 \(backslash)를 붙이면 된다.
```

- 문자열 선언

  - `변수명 = '문자열'` 로 선언가능
  - `print(str타입의 변수명)` 또는 `print('문자열')`을 사용하여 문자열을 출력할 수 있음

  ```python
  str1 = 'this is a "double" quotation test'	# 문자열 변수를 선언
  print(str1)					# 변수명을 넣어서 변수에 저장된 문자열을 출력
  print("this is string")		# 직접 문자열을 넣어서 출력
  
  - this is a "double" quotation test
  - this is string
  ```

  

- 문자열 연산자

  - `+ 더하기` : 문자열끼리 연결해서 문자열을 하나로 합쳐주는 연산자
  - `* 곱하기` : 곱한 수만큼 문자열을 반복해주는 연산자

  ```python
  a = 'Enjoy '
  b = 'python!'
  c = a + b		# 'Enjoy '와 'python!' 두 문자열이 합쳐져서 'Enjoy python!'이 c에 저장됨
  print(c)
  
  - Enjoy python!
  ```

  ```python
  a = 'hi '
  print(a * 3)		# 'hi'라는 문자열을 3번 반복해서 출력
  
  - hi hi hi 
  ```



### 4.3 리스트(List)

> 각각의 data를 묶어서 관리할 수 있는 자료형
>
> 관련된 데이터들을 개별적으로 관리하기 보다는 묶어서 관리했을 때 더욱 효율적임



- List 생성
  - 대괄호 `[  ]`를 이용해서 생성
  - 대괄호 안에 올 수 있는 항목(요소[Element])의 Data Type은 다양함
    - 숫자, 문자열, 불(Bool), 리스트(List), 튜플(Tuple), 세트(Set), 딕셔너리(Dictionary) 등 가능
    - 대괄호 안에 아무것도 쓰지 않으면 빈 리스트가 생성(데이터 type은 리스트)
  - 리스트를 생성시 각 항목의 Data Type은 같지 않아도 됨
  - 데이터는 입력한 순서대로 지정되며 각각의 항목들은 콤마`,`로 구분

```python
# 1번 학생의 국어, 영어, 수학, 과학 점수가 각각 90, 95, 85, 80점일 때 리스트 관리
student1 = [90, 95, 85, 80]	# list 생성시 [ ]로 묶어주고, 각각의 항목은 ,(콤마)로 구분
type(student1)

- list			# student1이라는 변수에 저장된 데이터 type은 list
```

```python
lst1 = []			# 비어있는 리스트
lst2 = [1,2,3,4,5]	# int형으로 구성되어있는 리스트
lst3 = ['H','E','L','L','O']	# str형으로 구성되어있는 리스트
lst4 = [1,'홍길동','M',95]		  # int형과 str형이 혼합되어있는 리스트
lst5 = ['수학','3반',[1, '홍길동', 'M']]		# 리스트 항목에 또다른 리스트를 생성
```

- List Indexing (리스트 인덱싱)

  > 리스트 항목을 각각 관리할 수 있도록 index가 붙여져있음
  >
  > Python에서 Index는 항상 0부터 시작

  - **변수명[0], 변수명[1], 변수명[2], ... 변수명[N-1]**로 개별 항목을 관리 할 수 있음

    - 마지막 항목을 **변수명[-1]**로 지정하고 왼쪽으로 갈수록 -1할 수 있음

    ![List1](C:\Users\sja95\OneDrive\바탕 화면\list3.png)

    - 리스트 항목으로 리스트를 생성한 경우에는 `변수명[A][B]` 으로 접근할 수 있음 

      ==> A번째 리스트에서 B번째 항목

    ![List2](C:\Users\sja95\OneDrive\바탕 화면\list4.png)

  ```python
  student1 = [90, 95, 85, 80]
  print(student1[0])			# student1의 0번 항목 90 출력
  print(student1[1])			# student1의 1번 항목 95 출력
  print(student1[-1])			# student1의 마지막 항목 80 출력
  
   - 90
   - 95
   - 80
  ```

  ```python
  lst = ['수학','3반',[1, '홍길동', 'M']]
  print(lst[0])			# lst의 0번 항목 수학 출력
  print(lst[1])
  print(lst[2])			# lst의 2번 항목인 리스트 출력
  print(lst[2][0])		# lst의 2번 항목 리스트의 0번 항목 1 출력
  print(lst[2][1])		# lst의 2번 항목 리스트의 1번 항목 홍길동 출력
  print(lst[2][2])		# lst의 2번 항목 리스트의 2번 항목 M 출력
  
   - 수학
   - 3반
   - [1, '홍길동', 'M']
   - 1
   - 홍길동
   - M
  ```

- **List의 특정 항목 수정**

  - `변수명[i] = new_data` : list의 i번 항목을 new_data 값으로 대입해서 수정
  - data type은 new_data type에 따라 변경됨 

  ```python
  student1 = [90, 95, 85, 80]
  student1[0] = '수학'			# student1 list의 0번 항목인 90을 '수학' str타입으로 변경
  print(student1)				
  
   - ['수학', 95, 85, 80]		# 변경된 student1 list
  ```

- **List 연산**

  - `+ (더하기)` : 두 list를 연결

  ```python
  list1 = ['국어', '수학', '영어']
  list2 = [90, 100, 85]
  list = list1 + list2		# list1과 list2를 연결해서 하나의 list를 생성
  print(list)
  
   - ['국어', '수학', '영어', 90, 100, 85]
  ```

  - `* (곱하기)` : list를 곱한 수만큼 반복

  ```python
  list1 = [1,2,3,4]
  list = list1 * 3		# lsit1을 3번 반복해서 하나의 list를 생성
  print(list)
  
   - [1, 2, 3, 4, 1, 2, 3, 4, 1, 2, 3, 4]
  ```

- **리스트 일부 항목 출력**

  - 각각의 항목을 출력하기 위해서는 `list명[i]`와 같이 index를 이용했음
  - index의 범위를 지정해 list의 일부 항목을 출력함
  - `list명[i_start : i_end]` : index가 i_start부터 i_end까지인 항목만을 출력
  - `list명[i_start : i_end : i_step]` : index가 start부터 end까지 step만큼 건너뛰며 항목 출력
    - i_start 생략시 0으로 간주 / i_end 생략시 n-1(마지막)으로 간주

  ```python
  list_data = [0,1,2,3,4,5,6,7,8,9]
  print(list_data)
  print(list_data[0:3])		# index 0부터 3까지의 항목을 출력
  print(list_data[4:8])		# index 4부터 8까지의 항목을 출력
  print(list_data[ :3])		# index 0부터 3까지의 항목을 출력
  print(list_data[7: ])		# index 7부터 마지막(9)까지의 항목을 출력
  print(list_data[::2])		# index 0(처음)부터 9(마지막)까지의 항목을 2개씩 건너뛰며 출력
  
   - [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
   - [0, 1, 2]
   - [4, 5, 6, 7]
   - [0, 1, 2]
   - [7, 8, 9]
   - [0, 2, 4, 6, 8]
  ```

- **리스트 항목 삭제**

  - `del list명[i]` : index가 i인 항목을 삭제

  ```python
  list_data = [0,1,2,3,4,5,6,7,8,9]
  print(list_data)
  del list_data[6]	# index가 6인 항목(6) 삭제
  print(list_data)
  del list_data[7]	# 수정된 list_data에서 index가 7인 항목(8) 삭제
  print(list_data)
  
   - [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
   - [0, 1, 2, 3, 4, 5, 7, 8, 9]
   - [0, 1, 2, 3, 4, 5, 7, 9]
  ```

- **list 항목 존재 여부 확인**

  - `항목 in list명` : list에서 해당 항목이 있는지 확인하고 있다면 True, 없다면 False를 return

  ``` python
  list_data = [0, 2, 4, 6, 8]
  print(4 in list_data)		# 4가 list_data에 있는지 확인 - True
  print(5 in list_data)		# 5가 list_data에 있는지 확인 - False
  
   - True
   - False
  ```

- **list method(리스트 메서드)**

  > Python에서 data type별로 이용할 수 있는 다양한 함수를 제공하는데, 이를 method(메서드)라고 함
  >
  > `자료형.매서드이름()` 형식으로 사용가능
  >
  > `변수명.매서드이름()` : data를 변수에 할당했을 경우, 변수명을 이용해서 method를 사용가능

  - `list명.append(new_data)` : list의 맨 마지막에 new_data를 추가

  ```python
  myFriends = ['James', 'Robert', 'Lisa', 'Mary']
  print(myFriends)	
  myFriends.append('Thomas')		# myFriends list 마지막에 'Thomas'항목을 추가
  print(myFriends)
  
   - ['James', 'Robert', 'Lisa', 'Mary']
   - ['James', 'Robert', 'Lisa', 'Mary', 'Thomas']
  ```

  - `list명.insert(i, new_data)` : list의 원하는 index 위치에 new_data를 추가
    - 기존 list에서 i이후 항목은 new_data가 삽입되므로 index가 1씩 증가

  ```python
  myFriends = ['James', 'Robert', 'Lisa', 'Mary']
  print(myFriends)	
  myFriends.insert(1, 'Paul')		# index가 1인 위치에 'Paul'을 삽입
  print(myFriends)
  
   - ['James', 'Robert', 'Lisa', 'Mary']
   - ['James', 'Paul', 'Robert', 'Lisa', 'Mary']
  ```

  - `list명.extend(['new_data1', 'new_data2', ...])` : list 마지막에 2개 이상의 new_data를 추가

  ```python
  myFriends = ['James', 'Robert', 'Lisa', 'Mary']
  print(myFriends)		
  myFriends.extend(['Laura', 'Betty', 'Steve'])	
  	# 주어진 리스트에 있는 data들을 myFriends list 마지막위치에 추가
  print(myFriends)
  
   - ['James', 'Robert', 'Lisa', 'Mary']
   - ['James', 'Robert', 'Lisa', 'Mary', 'Laura', 'Betty', 'Steve']
  ```

  - `list명.remove('data')` : list에서 'data'와 처음으로 일치하는 항목을 삭제

  ```python
  list = [1,2,3,4,5,2,3,6,7,1,2,4]
  list.remove(2)		# list에 2가 3번 들어있지만 그 중 첫번째 2가 삭제됨
  print(list)
  
   - [1, 3, 4, 5, 2, 3, 6, 7, 1, 2, 4]
  ```

  - `list명.pop()` : list의 마지막 항목을 제거한 후에 제거한 항목을 return

  ```python
  list = [1,2,3,4,5]
  poplist = list.pop()	# 마지막 항목인 5를 list에서 제거하고, return해서 poplist에 저장
  print(poplist)
  print(list)
   
   - 5
   - [1, 2, 3, 4]
  ```

  - `list명.index('data')` : list에서 해당 인자와 일치하는 첫 번째 항목의 위치 return

  ```python
  lst1 = ['James', 'Robert', 'Lisa', 'Mary', 'Steve', 'Thor']
  indexLisa = lst1.index('Lisa')	# Lisa는 index가 2인 항목이므로 index 2를 return
  print(indexLisa)
  
   - 2
  ```

  - `list명.count('data')` : list에서 해당 인자와 일치하는 항목이 몇 개인지 그 수를 return

  ```python
  lst2 = [1,1,1,2,3,4,4,4,5,5,6]
  cnt1 = lst2.count(1)		# data 값이 1인 항목의 개수를 return
  cnt2 = lst2.count(2)
  cnt3 = lst2.count(3)
  cnt4 = lst2.count(4)
  print(cnt1, cnt2, cnt3, cnt4)
  
   - 3 1 1 3
  ```

  - `list명.sort()` : 숫자나 문자열로 구성된 list에서 항목을 순방향으로 정렬

  ```python
  lst3 = [2,3,6,8,2,1,4,8,2,5,6,7]
  lst3.sort()		# lst3에서 내부적으로 항목을 정렬함
  print(lst3)		# 정렬된 lst3을 출력
  
   - [1, 2, 2, 2, 3, 4, 5, 6, 6, 7, 8, 8]
  ```

  - `list명.reverse()` : list 항목을 끝에서부터 역순으로 정렬

  ```python
  lst4 = [1,2,4,3,5,6,7,9,8]
  lst4.reverse()
  print(lst4)
  
   - [8, 9, 7, 6, 5, 3, 4, 2, 1]
  ```

  

### 4.4 Tuple(튜플)

> list와 유사하게 여러개의 data를 하나로 묶어서 관리
>
> list와 속성이 비슷하나, tuple data는 생성후에는 __수정이 불가능__함 ==> 상대적으로 처리 속도가 빠름



- __Tuple 생성__
  - 소괄호`(  )`를 이용하여 생성하거나 괄호 없이 data를 나열해서 생성
  - 항목은 list와 마찬가지로 콤마` , `로 구분
  - type()을 이용하여 tuple 자료형 확인 가능
  - 항목이 한 개인 tuple생성시 항목을 입력 후 반드시 콤마` , `를 입력

```python
tup1 = (1,2,3,4,)		# 소괄호() 를 사용해서 tuple생성 가능
tup2 = 'a','b','c','d'	# () 없이 항목들을 나열해서 tuple 생성 가능
tup3 = 10,
tup4 = (5,)				# 항목이 한 개인 tuple생성시에도 반드시 콤마(,)사용해야함

type(tup1) 	# 모두 type은 tuple
 
 - tuple
```

- __Tuple Method__

  - `index(data)` : 인자(data)와 일치하는 첫 번째 항목의 위치(index)를 반환

  ```python
  tup = ('a', 'b', 'c', 'd', 'c')
  tup.index('c')		# 첫 번째 c의 index인 2를 return
  
   - 2
  ```

  - `count(data)` : 인자(data)와 일치하는 항목의 개수를 반환

  ```python
  tup2 = ('a', 'a', 'b', 'b', 'c', 'c', 'c', 'a')
  tup2.count('a')		# 'a'라는 항목이 tup2에서 몇개가 있는지 count해서 그 수를 return
  
   - 3
  ```

  

### 4.5 Dictionary(딕셔너리)

> Key와 Value의 한 쌍으로 구성된 자료형
>
> index를 이용해 접근했던 list나 tuple과는 달리, dictionary는 key를 이용해 data값을 다룸

- __Dictionary 생성__

  - dictionary data 전체를 중괄호`{ }`로 묶어서 생성
  - Key는 숫자나 문자열 가능하지만 __중복은 불가능__함
  - Value는 중복, 숫자, 문자열, list, tuple, dictionary 등 다양한 형태가 가능
  - Key와 Value의 구분은 콜론` : `으로 하고, 각각의 쌍들은 콤마` , `로 구분

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  		# key : value 로 dictionary 요소를 정의해줌 각 쌍은 콤마(,)로 구분
  country_capital			# python에서는 print()함수를 사용하지 않고도 일부 알아서 출력해줌b
  
   - {'스위스': '베른', '영국': '런던', '프랑스': '파리', '호주': '멜버른'}
  		# dictionary는 입력순서와 출력순서가 다를 수 있음
  		# 순서보다는 key와 value의 쌍으로 data를 다뤄야할 때 주로 이용
  ```

  ```python
  dict1 = {1:'버스', 3:'비행기', 4:'택시', 5:'자전거'}
  		# key는 수, value는 문자열인 dictionary
  dict2 = {1:10, 2:20, 3:30, 4:40, 5:50}
  		# key, value 모두 수로 이루어진 dictionary
  dict3 = {"a":10, "b":20, "c":30, "d":40}
  		# key는 문자열, value는 수로 이루어진 dictionary
  dict4 = {'list1':[1,2,3], 'list2':[4,5,6], 'list3':[8,9,10]}
  		# value값으로 리스트도 가능
  ```

  

- __Dictionary 활용__

  - `type()` : dictionary type 확인

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  type(country_capital)
  
   - dict 		# dictionary type 확인
  ```

  - `dict명[Key]` : 지정한 Key의 Value를 return

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  country_capital['스위스'] 	# country_capital dictionary에서 '스위스'key의 Value 확인
  
   - '베른'
  ```

  - `dict명[new_Key] = new_Value` : 기존의 dictionary에 새로운 Key와 이와 대응되는 새로운 value 추가

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  country_capital["독일"] = "베를린"	# 새로운 Key(독일)과 Value(베를린)을 dictionary에 추가
  print(country_capital)	
  
  - {'영국': '런던', '프랑스': '파리', '스위스': '베른', '호주': '멜버른', '독일': '베를린'}
  ```

  - `dict명[Key] = new_Value` : 기존 dictionary에 있었던 key의 value값을 새롭게 변경

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  country_capital['호주'] = '캔버라'	# 호주 key의 value값을 '멜버른'에서 '캔버라'로 변경
  print(country_capital)
  
   - {'영국': '런던', '프랑스': '파리', '스위스': '베른', '호주': '캔버라'}
  ```

  - `del dict명[Key]` : 기존 dictionary의 해당 Key와 이와 대응되는 Value를 삭제

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  del country_capital["프랑스"]		# 프랑스라는 key를 찾아 key와 그의 value값까지 모두 삭제
  print(country_capital)
  
   - {'영국': '런던', '스위스': '베른', '호주': '멜버른'}
  ```

  - `dict명.keys()` : 해당 dictionary의 Key 전체를 list 형태로 반환

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  country_capital.keys()		# country_capital dict에 존재하는 모든 Key를 list로 return
  
   - dict_keys(['영국', '프랑스', '스위스', '호주'])
  ```

  - `dict명.values()`: 해당 dictionary의 Value 전체를 list 형태로 반환

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  country_capital.values()	# country_capital dict에 존재하는 모든 Value를 list로 return
  
   - dict_values(['런던', '파리', '베른', '멜버른'])
  ```

  - `dict명.items()` : 해당 dictionary의 모든 Key, Value를 tuple 형식(Key, Value)으로 반환

  ```python
  country_capital = {'영국':'런던', '프랑스':'파리', '스위스':'베른', '호주':'멜버른'}
  country_capital.items()	# country_capital dict에 있는 모든 Key, Value를 tuple로 return
  
   - dict_items([('영국', '런던'), ('프랑스', '파리'), ('스위스', '베른'), ('호주', '멜버른')])
  ```

  - `dict명.update(new_dict)` : 해당 dictionary에 new_dict를 추가

  ```python
  fruit1 = {'사과':1, '배':2, '오렌지':3, '딸기':4, '자몽':5}
  fruit2 = {'바나나':10, '포도':11, '블루베리':12}
  fruit1.update(fruit2)	# fruit1에 fruit2 dictionary의 data들을 그대로 추가
  print(fruit1)
  
   - {'사과': 1, '배': 2, '오렌지': 3, '딸기': 4, '자몽': 5, '바나나': 10, '포도': 11, 
      '블루베리': 12}
  ```

  - `dic명.clear()` : 해당 dictionary의 모든 Key, Value을 삭제

  ```python
  fruit1 = {'사과':1, '배':2, '오렌지':3, '딸기':4, '자몽':5}
  fruit1.clear()		# fruit1의 모든 항목들이 모두 삭제됨
  print(fruit1)
  
   - {}		# type은 dict으로 그대로 유지. dictionary의 data만 삭제됨
  ```

