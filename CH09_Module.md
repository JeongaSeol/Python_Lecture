# Python CH.09 Module

> 코드를 작성한 후 파일로 저장하면 다른 코드에서도 
>
> 저장된 파일의 변수, 함수, 클래스 등을 이용할 수 있음
>
> python에서 코드가 저장된 파일을 모듈(Module)이라고 함
>
> 이미 만들어진 모듈을 활용하여 코드를 효과적으로 작성 가능



## 9.1 모듈(Module)을 사용하는 이유

- #### 코드 작성과 관리가 쉬워짐

  - 대규모 프로그램을 만들 때, 보통 파일 하나에 전체 코드를 구현하지 않고 기능별로 나눠 코드 구현을 함
  - 하나의 코드 파일에서는 해당 기능의 구현에만 집중할 수 있으므로 코드 작성과 관리가 쉬움

- #### 이미 작성된 코드를 재사용할 수 있음

  - 작업을 위해 만들어 놓은 모듈은 다른 작업 시 활용 가능
  - 특정 기능을 구현한 모듈은 다른 프로그램 작성 시  재사용 가능
  - 이미 구현된 코드를 재사용하므로 시간이나 비용이 절약됨
  - 자신이 만든 것 뿐 아니라 다른 사람이 만든 모듈도 사용 가능

- #### 공동 작업을 효율적으로, 편리하게 할 수 있음

  - 대규모 프로그램 만들 때, 일반적으로 여러 사람이 같이 작업을 진행
  - 공동 프로그램 제작 시 전체 프로그램을 모듈별로 설계, 개인별로 나누어 코딩 후 전체 모듈 통합
  - 모듈별로 구분해서 코드를 작성시 자신이 담당하는 모듈만 집중해서 개발 할 수 있으므로 
    공동 작업으로 인한 복잡성이 줄어들고 효율은 높아짐



## 9.2 모듈(Module) 생성 및 호출

- `모듈이름.py` : python 코드가 저장된 파일을 모듈이라 하고, 확장자는 `.py`

- 모듈이 저장된 위치(경로)에서 python을 실행하여 코드를 작성하거나
  python 코드 파일을 실행해서 저장된 모듈 활용

- 모듈과 같은 위치에 있지 않더라도 모듈이 저장된 위치(경로)를 지정해서 사용 가능

  

- #### 코드를 파일로 저장

  - `%%writefile [-a] file명.py` : 코드 셀의 코드를 python 코드 파일로 저장하기
  - `%%load file명.py` : 저장된 python 코드 파일을 불러오기
  - `%%run file명.py` : python 코드 파일 실행하기

  ```python
  ## my_first_module.py 모듈을 작성해서 작업 폴더에 저장하기
  --------------------------<코드>-----------------------------
  
  %%writefile my_first_module.py
  
  def my_function() :
  	print("This is my first module.")
  ```

  ![module1](C:\Users\sja95\OneDrive\바탕 화면\module1.png)

  ```python
  ## my_first_module.py이 잘 생성되었는지 코드로 확인
  --------------------------<코드>-----------------------------
  
  !cat my_first_module.py
  
  --------------------------<결과>-----------------------------
  def my_function() :
  	print("This is my first module.")
  ```

- #### 모듈 불러오기

  - `import 모듈명` : 생성된 모듈을 사용
    - `모듈명.변수` / `모듈명.함수()` / `모듈명.클래스()`와 같은 형식으로 모듈에서 정의한 변수/함수/클래스
      사용 가능
    - 반복적으로 호출할 때마다 계속 모듈명을 써야하므로 불편함
  - `import 모듈명 as 별명` : 코드 작성시 `모듈명.변수` 대신 `별명.변수` 등으로 사용 가능
  - `dir(모듈명)` : 불러온 모듈에서 사용할 수 있는 변수, 함수, 클래스를 확인

  ```python
  ## my_first_module 모듈을 불러서 모듈의 함수를 실행하기
  --------------------------<코드>-----------------------------
  
  import my_first_module
  
  my_first_module.my_function()		# my_first_module 모듈에서 정의된 함수 호출해서 사용
  									# 모듈명.함수() 형식으로 사용
  
  --------------------------<결과>-----------------------------
  This is my first module.
  ```

  ```python
  ## my_first_moduel 모듈을 mf라는 별명을 붙인 뒤 모듈에서 정의된 함수 호출하기
  --------------------------<코드>-----------------------------
  
  import my_first_module as mf
  
  mf.my_function()		# 별명인 mf.함수()를 사용해서 간편하게 호출 할 수 있음
  
  --------------------------<결과>-----------------------------
  This is my first module.
  ```

  ```python
  ## my_first_module 모듈의 변수 / 함수 / 클래스 확인하기
  --------------------------<코드>-----------------------------
  
  dir(my_first_module)
  
  --------------------------<결과>-----------------------------
  ['__builtins__',
   '__cached__',
   '__doc__',
   '__file__',
   '__loader__',
   '__name__',
   '__package__',
   '__spec__',
   'my_function']		# my_first_module에서 정의된 함수를 확인 할 수 있음
  ```

  ```python
  ## 모듈 생성 및 호출하기 실습
  --------------------------<코드>-----------------------------
  
  %%writefile my_area.py
  
  PI=3.14
  def square_area(a) :
  	return a**2			# 정사각형 넓이 return
  	
  def circle_area(r) :
  	return PI*r**2		# 원의 넓이 return
  ------------------------------------------------------------
  
  import my_area
  
  print('pi = ', my_area.PI)
  print('square area = ', my_area.square_area(5))	#모듈 함수 사용
  print('circle_area = ', my_area.circle_area(2)) 
  
  --------------------------<결과>-----------------------------
  pi =  3.14
  square area =  25
  circle area =  12.56
  ```

  - `from 모듈명 import 변수명`  / `from 모듈명 import 함수명` / `from 모듈명 import 클래스명`
    	: 모듈 내에 있는 변수 / 함수 / 클래스를 `모듈명.`없이 직접 호출해서 사용 가능
    - 콤마`,`로 구분해서 여러 개를 선언 가능
  - `from 모듈명 import 변수명/함수명/클래스명 as 별명` : 변수명/함수명/클래스명 대신 별명으로 사용
  - `from 모듈명 import *` : 호출하는 모듈의 모든 변수, 함수, 클래스를 바로 사용
    - 편리하긴 하지만 모듈을 두 개 이상 사용할 때는 주의가 필요

  ```python
  ## 모듈 호출해서 변수 바로 사용하기
  --------------------------<코드>-----------------------------
  
  from my_area import PI
  print('pi = ', PI)		# my_area.PI 대신 PI만 써서 사용 가능
  
  --------------------------<결과>-----------------------------
  pi = 3.14
  ```

  ```python
  ## 모듈 호출해서 함수 바로 사용하기
  --------------------------<코드>-----------------------------
  
  from my_area import square_area
  from my_area import circle_area
  
  print('square area = ', square_area(5))
  print('circle area = ', circle_area(2))
  
  --------------------------<결과>-----------------------------
  square area =  25
  circle area =  12.56
  ```

  ```python
  ## 불러오려는 변수와 함수를 콤마(,)로 구분하여 한 번에 여러 개 선언
  --------------------------<코드>-----------------------------
  
  from my_area import PI, square_area, circle_area
  
  print('pi = ', PI)
  print('square area = ', square_area(5))
  print('circle area = ', circle_area(2))
  
  --------------------------<결과>-----------------------------
  pi =  3.14
  square area =  25
  circle area =  12.56
  ```

  ```python
  ## 변수/함수를 별명을 사용해서 호출
  --------------------------<코드>-----------------------------
  
  from my_area import PI as pi				# PI변수를 pi로 
  from my_area import square_area as square	# square_area 함수를 square로
  from my_area import circle_area as circle	# circle_area 함수를 circle로 이용
  
  print('pi = ', pi)
  print('square area = ', square(5))
  print('circle area = ', circle(2))
  
  --------------------------<결과>-----------------------------
  pi =  3.14
  square area =  25
  circle area =  12.56
  ```

  ```python
  ## *를 이용하여 모듈 내에서 정의되어 있는 변수, 함수, 클래스를 모두 불러와서 사용하기
  --------------------------<코드>-----------------------------
  
  from my_area import *			# 모든 변수, 함수, 클래스 불러오기 
  
  print('pi = ', PI)
  print('square area = ', square_area(5))
  print('circle area = ', circle_area(2))
  
  --------------------------<결과>-----------------------------
  pi =  3.14
  square area =  25
  circle area =  12.56
  ```

- #### 모듈 불러오기 주의 사항

> 두 개 이상의 모듈을 불러와서 그 안에 정의되어 있는 변수, 함수, 클래스를 사용할 때, 
>
> 동일한 함수명을 가진 함수가 각각 모듈에서 정의되어 있다면 
>
> 호출한 함수는 어떤 모듈에서 정의된 함수일까?

  - 모듈 중에서 __나중에 선언__해서 불러온 모듈의 함수가 호출됨

```python
## my_module1에서는 func1() / func2() 를 정의함
## my_module2에서는 func2() / func3() 을 정의함
--------------------------<코드>-----------------------------

%%writefile my_module1.py

def func1() :
	print('func1 in my_module1')

def func2() :
	print('func2 in my_module1')
	
------------------------------------------------------

%%writefile my_module2.py

def func2() :
	print('func2 in my_module2')
	
def func3() :
	print('func3 in my_module2')
	
------------------------------------------------------
## my_module1과 my_module2를 불러오고, 함수 func1(), func2(), func3()을 호출
--------------------------<코드>-----------------------------

from my_module1 import *
from my_module2 import *

func1()
func2()
func3()

--------------------------<결과>-----------------------------
func1 in my_module1
func2 in my_module2				# 나중에 불러온 my_module2에서의 함수 func2()가 호출됨
func3 in my_module2
```

```python
## my_module2를 먼저 불러오고, 그 다음 my_module1을 불러서 다시 함수 호출
--------------------------<코드>-----------------------------

from my_module2 import *
from my_module1 import *

func1()
func2()
func3()

--------------------------<결과>-----------------------------
func1 in my_module1
func2 in my_module1				# 나중에 불러온 my_module1에서의 함수 func2()가 호출됨
func3 in my_module2
```

- #### 모듈 실행하기

  - 모듈에서 코드를 직접 수행하는 경우와 import해서 사용하는 경우를 구분해서 코드를 실행

  - `if__ name __ == '__ main__' :` 

    ​		`< 모듈을 직접 수행할 때만 실행되는 코드>` 

    `else :`

    ​		`< 모듈을 import 했을 때만 실행되는 코드>` 

    - 위와 같이 if문 구조를 사용해서 모듈을 직접 실행(`%run`)했을 때 실행되는 코드와 import했을 때 실행되는 코드를 구분할 수 있음

  ```python
  ## my_module_test.py 모듈을 직접 수행해보고, import 했을 때와 어느 코드가 실행되는지 확인
  --------------------------<코드>-----------------------------
  
  %%writefile my_module_test.py			# 모듈 생성 및 저장
  
  def func(a) :
  	print("입력 숫자 :", a)
  	
  if __name__ == "__main__" :			# 모듈이 직접 수행했을 때
  	print("모듈을 직접 실행")
  	func(3)
  	func(4)
  else :								# 모듈이 직접 수행되지 않았을 때 == import 했을 때
  	print("모듈을 import해서 실행")
  
  ---------------------------------------------------
  ## 모듈을 직접 수행
  --------------------------<코드>-----------------------------
  
  %run my_module_test.py			# 모듈 직접 수행
  
  --------------------------<결과>-----------------------------
  모듈을 직접 실행
  입력 숫자 :  3
  입력 숫자 :  4
  ---------------------------------------------------
  ## 모듈을 import해서 수행
  --------------------------<코드>-----------------------------
  
  import my_module_test			# 모듈 import
  
  --------------------------<결과>-----------------------------
  모듈을 import해서 실행
  ```



## 9.3 내장 모듈(Module)

- `random` : 임의로 숫자(난수)를 발생

  - `import random` 으로 random 모듈을 불러온 후에 random 모듈의 함수를 이용

  | Random 모듈 함수               | 설명                                                         | 사용 예                      |
  | ------------------------------ | ------------------------------------------------------------ | ---------------------------- |
  | random()                       | 0.0 <= x <= 1.0 범위의 임의의 실수 return                    | random.random()              |
  | randint(a,b)                   | a <= x <=b 범위의 임의의 정수 return                         | random.randint(1,6)          |
  | randrange([start],stop[,step]) | start <= x <= stop (step단위로) 에서 임의의 정수 return      | random.randrange(0,10,2)     |
  | choice(seq)                    | 공백이 아닌 시퀀스(seq)에서 임의의 항목 return               | random.choice([1,2,3])       |
  | sample(population,k)           | 시쿼스로 이뤄진 모집단(population)에서 중복되지 않는 k개의 인자 return | random.sample([1,2,3,4,5],2) |

  ```python
  ## 특정 범위의 정수 안에서 임의의 정수를 발생시키는 randint()함수 이용
  --------------------------<코드>-----------------------------
  
  import random			# random 모듈을 import 해주어야 randint()함수 사용 가능
  
  dice1 = random.randint(1,6)		# 1부터 6까지 중 임의의 정수 생성
  dice2 = random.randint(1,6)
  print('주사위 두 개의 숫자 : {0}, {1}'.format(dice1,dice2))
  
  --------------------------<결과>-----------------------------
  주사위 두 개의 숫자 : 3, 5		# 난수를 발생하므로 실행할 때마다 결과는 달라짐
  ```

  ```python
  ## 정해진 범위 안에서 특정 수 만큼 차이가 나는 정수를 발생 시키는 randrange() 함수 이용
  --------------------------<코드>-----------------------------
  
  import random 			# randrange()함수 이용하기 위해 random 모듈 import
  
  random.randrange(0,11,2)	# 0부터 10까지(11-1) 범위 중 짝수를 발생
  
  --------------------------<결과>-----------------------------
  10		# 난수를 발생하므로 실행할 때마다 결과는 달라짐
  ------------------------------------------------------------------------------
  ## 홀수를 발생시키거나 10단위 등 설정한 단위의 숫자를 발생시킬 때도 이용
  --------------------------<코드>-----------------------------
  
  import random 			# randrange()함수 이용하기 위해 random 모듈 import
  
  num1 = random.randrange(1,10,2)	# 1~9중에서 임의의 홀수 
  num2 = random.randrange(0,100,10) # 0~99중에서 임의의 10 단위 숫자 
  
  print("num1 : {0}, num2 : {1}".format(num1, num2))
  
  --------------------------<결과>-----------------------------
  num1 : 7, num2 : 40
  ```

  ```python
  ## 시퀀스(list, tuple) 데이터에서 임의의 항목을 하나 선택할 때 choice()함수 이용
  --------------------------<코드>-----------------------------
  
  import random 			# choice()함수 이용하기 위해 random 모듈 import
  
  menu = ['비빔밥', '된장찌개', '볶음밥', '불고기', '스파게티', '피자', '탕수육']
  random.choice(menu)
  
  --------------------------<결과>-----------------------------
  '피자'
  ```

- `datetime`: 날짜 및 시간 관련 처리

- `calendar` : 년도/월/주 등 달력과 관련된 처리

- 이 밖에 python 표준 라이브러리에 관한 설명 : [python_표준라이브러리](https://docs.python.org/3.9/library/)

- 
