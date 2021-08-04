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

  - `import datetime`으로 모듈 불러온 후에는 클래스에서 객체를 생성해 이용하는 방법과 
    	각 클래스의 클래스 메서드를 이용하는 방법이 있음
  - 생성한 객체를 이용해서 각 클래스의 속성을 이용 
    - date 클래스에는 year, month, day의 속성, time 클래스에서는 hour, minute, second 속성이 존재
    - 연도, 월, 일 각각 구하기 위해서는 date 클래스의 속성(year, month, day)를 이용 가능
    - date 객체의 type은 __date__. 그 객체끼리 빼기 연산 가능
      - 빼기연산으로 양수 / 음수의 결과가 나오고, 연산 후 데이터 type은 __timedelta__ 바뀜

  ```python
  ## 각 클래스에서 객체를 생성해서 이용하는 방법
  --------------------------<코드>-----------------------------
  
  import datetime
  
  date_obj = datetime.date(year, month, day)			# 년, 월, 일 (날짜)
  time_obj = datetime.time(hour, minute, second)		# 시, 분, 초 (시간)
  datetime_obj = datetime.datetime(year, month, day, hour, minute, second) # 날짜와 시간
  
  ```

  - 각 클래스의 클래스 메서드를 이용
    - 클래스 메서드를 이용하는 경우에도 각 클래스의 속성은 그대로 이용
    - `datetime.date.today()` : 오늘 날짜를 return
    - `datetime.datetime.now()` : 오늘날짜와 현재 시각을 return
    - `{: %Y %m %d %H %M %S}` : 각각 연도, 월, 일, 시, 분, 초를 출력양식을 지정해 출력(__대소문자 주의__) 

  ```python
  ## 객체를 생성하지 않고, 각 클래스의 클래스 메서드를 이용하는 방법
  --------------------------<코드>-----------------------------
  
  import datetime
  
  date_var = datetime.date.date_classmethod()
  time_var = datetime.time.time_classmethod()
  datetime_var = datetime.datetime.datetime_classmethod()
  ```

  ```python
  ## (실전) date, time, datetime 클래스 이용
  --------------------------<코드>-----------------------------
  
  import datetime
  
  set_day = datetime.date(2021,8,4)		# date객체 생성
  print(set_day)
  
  --------------------------<결과>-----------------------------
  2021-08-04
  ```

  ```python
  ## 년도, 월, 일을 각각 구하기 위해 date 클래스의 속성(year, month, day)사용
  --------------------------<코드>-----------------------------
  
  import datetime
  
  set_day = datetime.date(2021,8,4)		# date객체 생성
  print('{0}/{1}/{2}'.format(set_day.year, set_day.month, set_daty.day))
  
  --------------------------<결과>-----------------------------
  2021/8/4
  ```

  ```python
  ## date객체끼리의 연산 및 데이터type 확인
  --------------------------<코드>-----------------------------
  
  import datetime
  
  day1 = datetime.date(2021,4,1)
  day2 = datetime.date(2021,7,10)
  diff_day = day2 - day1				# date 객체끼리 빼기 연산
  print('day2-day1 = ', diff_day)
  
  print(type(day1))
  print(type(diff_day))		# 데이터 타입 확인
  
  --------------------------<결과>-----------------------------
  day2 - day1 =  100 days, 0:00:00
  <class 'datetime.date'>
  <class 'datetime.timedelta'>		# 빼기연산 후에는 timedelta 타입으로 바뀜
  ```

  ```python
  ## 빼기연산 후 날짜만 출력하려면 timedelta 클래스속성인 days를 이용
  --------------------------<코드>-----------------------------
  
  import datetime
  
  day1 = datetime.date(2021,4,1)
  day2 = datetime.date(2021,7,10)
  diff_day = day2 - day1				
  print('day2-day1 = ', diff_day)		# 날짜에 시,분,초까지 출력
  
  print("** 지정된 두 날짜의 차이는 {0}일입니다.".format(diff_day.days)) # 날짜만 출력
  
  --------------------------<결과>-----------------------------
  day2 - day1 =  100 days, 0:00:00
  ** 지정된 두 날짜의 차이는 100일입니다
  ```

  ```python
  ## 오늘 날짜를 확인하고, 특정 날짜와의 뺴기 연산 수행
  --------------------------<코드>-----------------------------
  
  import datetime
  
  today = datetime.date.today()
  sp_day = datetime.date(2020,12,31)
  print(today)
  print('오늘은 {0}로 부터 {1}일째 되는 날입니다.'.format(sp_day, (today-sp_day).days))
  
  --------------------------<결과>-----------------------------
  2021-08-04
  오늘은 2020-12-31로 부터 216일째 되는 날입니다.
  ```

  ```python
  ## 시간을 처리하는 time 클래스
  --------------------------<코드>-----------------------------
  
  import datetime
  
  set_time = datetime.time(15, 30, 45)
  print(set_time)
  
  --------------------------<결과>-----------------------------
  15:30:45
  ```

  ```python
  ## time 클래스의 속성(hour, minute, second)을 이용하여 시, 분, 초를 각각 출력
  --------------------------<코드>-----------------------------
  
  print('{0}시{1}분{2}초'.format(set_time.hour, set_time.minute, set_time.second))
  
  --------------------------<결과>-----------------------------
  15:30:45
  15시30분45초
  ```

  ```python
  ## 날짜와 시간 모두 다룰 수 있는 datetime 클래스
  --------------------------<코드>-----------------------------
  
  import datetime
  
  set_dt = datetime.datetime(2021,8,4,11,37,0)	# datetime은 모듈. datetime()은 클래스
  print(set_dt)
  
  --------------------------<결과>-----------------------------
  2021-08-04 11:37:00
  ```

  ```python
  ## 클래스 속성을 이용하여 연, 월, 일, 시, 분, 초를 각각 다룸
  --------------------------<코드>-----------------------------
  
  import datetime
  
  set_dt = datetime.datetime(2021,8,4,11,37,0)	
  print('날짜 {0}/{1}/{2}'.format(set_dt.year, set_dt.month, set_dt.day))
  print('시각 {0}:{1}:{2}'.format(set_dt.hour, set_dt.minute, set_dt.second))
  
  --------------------------<결과>-----------------------------
  날짜 2021/8/4
  시각 11:37:0
  ```

  ```python
  ## now() 메서드를 이용하여 오늘 날짜, 현재 시각을 구함
  --------------------------<코드>-----------------------------
  
  import datetime
  
  now = datetime.datetime.now()
  print(now)
  
  --------------------------<결과>-----------------------------
  2021-08-04 02:42:17.936355			# 소수점 이하 6째자리까지의 초까지 return
  ```

  ```python
  ## 출력 양식을 지정하여 년, 월, 일, 시, 분, 초를 각각 출력
  --------------------------<코드>-----------------------------
  
  import datetime
  
  now = datetime.datetime.now()
  print("Date & Time : {:%Y-%m-%d	 %H:%M:%S}".format(now))
  		# 출력양식은 반드시 {: }안에 있어야 하며 일부만 사용할 수도 있음
  
  --------------------------<결과>-----------------------------
  Date & Time : 2021-08-04  02:48:38
  ```

  ```python
  ## datetime 객체의 빼기 연산
  --------------------------<코드>-----------------------------
  
  import datetime
  
  now = datetime.datetime.now()
  set_dt = datetime.datetime(2020,12,1,12,30,45)
  
  print('현재 날짜 및 시각 : ', now)
  print('차이 : ', set_dt - now)
  
  --------------------------<결과>-----------------------------
  현재 날짜 및 시각 :  2021-08-04 02:50:16.153746
  차이 :  -246 days, 9:40:28.846254
  ```

  ```python
  ## from 모듈명 import 클래스명 방법을 이용해서 바로 클래스 이름/메서드 이름으로 이용가능
  --------------------------<코드>-----------------------------
  
  from datetime import date, time, datetime
  
  print(date(2021,7,1))
  print(date.today())
  print(time(15,30,45))
  print(datetime(2021,2,14,18,10,50))
  print(datetime.now())
  
  --------------------------<결과>-----------------------------
  2021-07-01
  2021-08-04
  15:30:45
  2021-02-14 18:10:50
  2021-08-04 04:33:39.135897
  ```

- `calendar` : 다양한 형태로 달력을 생성해서 출력하고 날짜와 관련된 정보(연도, 월, 주)를 구하는 방법

  | calendar 모듈함수         | 설명                                                         | 사용예                           |
  | ------------------------- | ------------------------------------------------------------ | -------------------------------- |
  | calendar(year[,m=3])      | 지정된 연도(year)의 전체 달력을 문자열로 return  (기본형식은 3개의 열) | calendar.calendar(2021)          |
  | month(year, month)        | 지정된 연도(year)와 월(month)의 달력을 문자열로 return       | calendar.month(2021,8)           |
  | monthrange(year,month)    | 지정된 연도(year)와 월(month)의 시작 요일과 일수 return (요일의 경우 0[월요일]~6[일요일]) 사이의 숫자로 return | calendar.monthrange(2021,8)      |
  | firstweekday()            | 달력에 표시되는 주의 첫 번째 요일값을 return. 기본값으로는 월요일(0)으로 지정됨 | calendar.firstweekday()          |
  | setfirstweekdaty(weekday) | 달력에 표시되는 주의 첫 번째 요일을 지정                     | calendar.setfirstweekday(6)      |
  | weekday(year, month, day) | 지정된 날짜[연도(year), 월(month), 일(day)]의 요일을 return  | calendar.weekday(year,month,day) |
  | isleap(year)              | 지정된 연도(year)가 윤년인지를 판단해 윤년이면 True, 아니면 False를 return | claendar.isleap(2020)            |

  - calendar 모듈의 주요 __요일 지정 상수__

  |  요일  |    요일지정상수    | 숫자로표시 |
  | :----: | :----------------: | :--------: |
  | 월요일 |  calendar.MONDAY   |     0      |
  | 화요일 |  calendar.TUESDAY  |     1      |
  | 수요일 | calendar.WEDNESDAY |     2      |
  | 목요일 | calendar.THURSDAY  |     3      |
  | 금요일 |  calendar.FRIDAY   |     4      |
  | 토요일 | calendar.SATURDAY  |     5      |
  | 일요일 |  calendar.SUNDAY   |     6      |

  ```python
  ## calendar()를 이용하여 지정한 연도의 전체 달력을 출력하기
  --------------------------<코드>-----------------------------
  
  import calendar
  
  print(calendar.calendar(2021))
  
  --------------------------<결과>-----------------------------
    									2021
  
        January                   February                   March
  Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
               1  2  3       1  2  3  4  5  6  7       1  2  3  4  5  6  7
   4  5  6  7  8  9 10       8  9 10 11 12 13 14       8  9 10 11 12 13 14
  11 12 13 14 15 16 17      15 16 17 18 19 20 21      15 16 17 18 19 20 21
  18 19 20 21 22 23 24      22 23 24 25 26 27 28      22 23 24 25 26 27 28
  25 26 27 28 29 30 31                                29 30 31
  
         April                      May                       June
  Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
            1  2  3  4                      1  2          1  2  3  4  5  6
   5  6  7  8  9 10 11       3  4  5  6  7  8  9       7  8  9 10 11 12 13
  12 13 14 15 16 17 18      10 11 12 13 14 15 16      14 15 16 17 18 19 20
  19 20 21 22 23 24 25      17 18 19 20 21 22 23      21 22 23 24 25 26 27
  26 27 28 29 30            24 25 26 27 28 29 30      28 29 30
                            31
  
          July                     August                  September
  Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
            1  2  3  4                         1             1  2  3  4  5
   5  6  7  8  9 10 11       2  3  4  5  6  7  8       6  7  8  9 10 11 12
  12 13 14 15 16 17 18       9 10 11 12 13 14 15      13 14 15 16 17 18 19
  19 20 21 22 23 24 25      16 17 18 19 20 21 22      20 21 22 23 24 25 26
  26 27 28 29 30 31         23 24 25 26 27 28 29      27 28 29 30
                            30 31
  
        October                   November                  December
  Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su      Mo Tu We Th Fr Sa Su
               1  2  3       1  2  3  4  5  6  7             1  2  3  4  5
   4  5  6  7  8  9 10       8  9 10 11 12 13 14       6  7  8  9 10 11 12
  11 12 13 14 15 16 17      15 16 17 18 19 20 21      13 14 15 16 17 18 19
  18 19 20 21 22 23 24      22 23 24 25 26 27 28      20 21 22 23 24 25 26
  25 26 27 28 29 30 31      29 30                     27 28 29 30 31
  
  # 출력 양식은 달을 3열로 출력
  ```

  ```python
  ## 달의 출력 양식을 변경
  --------------------------<코드>-----------------------------
  
  import calendar
  
  print(calendar.calendar(2021, m=4))
  
  --------------------------<결과>-----------------------------
  ```

  ![calendar()](C:\Users\sja95\OneDrive\바탕 화면\calendar module.PNG)

  ```python
  ## month()함수를 이용하여 지정한 연도의 특정 월만 출력
  --------------------------<코드>-----------------------------
  
  import calendar
  
  print(calendar.month(2021,9))
  
  --------------------------<결과>-----------------------------
     September 2021
  Mo Tu We Th Fr Sa Su
         1  2  3  4  5
   6  7  8  9 10 11 12
  13 14 15 16 17 18 19
  20 21 22 23 24 25 26
  27 28 29 30
  ```

  ```python
  ## monthrange()함수를 이용해 연도와 월을 지정하고 그달 1일이 시작하는 요일과 그 달의 날짜 수 알기
  --------------------------<코드>------------------------------------------------------
  
  import calendar
  
  calendar.monthrange(2021,2)
  
  --------------------------<결과>------------------------------------------------------
  (0, 28)	# 0은 월요일 / 2월은 28일로 구성됨
  ```

  ```python
  ## firstweekday() 함수를 실행하여 일주일의 시작요일을 확인
  --------------------------<코드>-------------------------
  import calendar
  
  calendar.firstweekday()
  
  --------------------------<결과>-------------------------
  0	 #일주일의 시작요일이 월요일로 지정되어있는 것을 확인
  ```

  ```python
  ## setfirstweekday(weekday)함수를 이용하여 일주일의 시작 요일을 지정
  --------------------------<코드>-----------------------------
  
  import calendar
  
  calendar.setfirstweekday(calendar.SUNDAY) # 혹은 setfirstweekday(6)이라고 입력 가능
  print(calendar.month(2021,8))
  
  --------------------------<결과>-----------------------------
     August 2021
  Su Mo Tu We Th Fr Sa
   1  2  3  4  5  6  7
   8  9 10 11 12 13 14
  15 16 17 18 19 20 21
  22 23 24 25 26 27 28
  29 30 31					# 시작 요일이 일요일로 바뀌었음
  ```

  ```python
  ## weekday()함수를 이용하여 해당 날짜의 요일을 확인하기
  --------------------------<코드>-----------------------------
  
  import calendar
  
  print(calendar.weekday(2021, 8, 4))
  
  --------------------------<결과>-----------------------------
  2 		# 2 == 수요일
  ```

  ```python
  ## isleap(year)함수를 이용하여 해당 연도가 윤년인지를 확인하기
  --------------------------<코드>-----------------------------
  
  import calendar
  
  print(calendar.isleap(2020))	# 2020은 윤년
  print(calendar.isleap(2021))	# 2021은 윤년이 아님
  
  --------------------------<결과>-----------------------------
  True
  False
  ```

- 이 밖에 python 표준 라이브러리에 관한 설명 : [python_표준라이브러리](https://docs.python.org/3.9/library/)



## 9.4 패키지(Package)

> 하나의 기능을 구현할 때 여러 개의 모듈로 구현하는 경우가 많음
>
> 여러 모듈을 체계적으로 모아 놓은 패키지로 관리하면 더욱 효율적
>
> python package는 여러 모듈을 폴더로 묶어서 계층적으로 관리



- #### 패키지 구조

  - 폴더 구조로 되어 있음. 각 폴더에는 `__init__.py`라는 파일이 존재함
  - `__init__.py` 
    - 해당 폴더가 패키지의 일부인 것을 알려주는 역할을 함
    - 패키지를 초기화하는 코드를 넣을 수도 있고, 아무 코드도 없는 빈 파일일 수도 있음
    - 패키지 생성시 이 파일이 없어도 되지만 하위 호환성을 고려하여 포함하는 것을 추천

  ```python
  ## imgread 모듈에는 pngread()함수와 jpgread() 함수를 생성
  --------------------------<코드>-----------------------------
  
  %%writefile image/io_file/imgread.py 	# image패키지 안 io_file 폴더 안에 imgread.py생성
  
  def pngread() :
  	print("pngread in imgread module")
  
  def jpgread() :
  	print("jpgread in imgread module")
  ```

- #### 패키지 사용

  - `import 패키지 내 모듈명` : 해당 패키지 모듈을 이용
    - `import 패키지명.모듈명` : 패키지 폴더 안에 바로 모듈이 있는 경우
    - `import 패키지명.폴더명.모듈명` : 패키지와 모듈 사이에 폴더가 있는 경우

  ```python
  ## image 패키지 io_file 폴더의 imgread 모듈 import
  --------------------------<코드>-----------------------------
  
  import image.io_file.imgread	
  
  image.io_file.imgread.pngread()	# imgread 모듈 내의 pngread()함수 호출
  image.io_file.imgread.jpgread() # imgread 모듈 내의 jpgread()함수 호출
  ```

  - `from 패키지[.폴더명] import 모듈명` : 모듈 내 함수를 더 간단하게 호출하기 위한 방법

  ```python
  ## imgread 모듈 내 pngread() / jpgread()함수 간단하게 사용하기
  --------------------------<코드>-----------------------------
  
  from image.io_file import imgread
  
  imgread.pngread()
  imgread.jpgread()		# 패키지명.폴더명.모듈명.함수명 보다는 더 간단하게 표현 가능
  ```

  - `from 패키지[.폴더명].모듈명 import 사용할 함수명` : 모듈 내 함수를 더 간단하게 호출

  ```python
  ## 더 간단하게 사용
  --------------------------<코드>-----------------------------
  
  from image.io_file.imgread import pngread
  
  pngread()		# 모듈명.함수명 하지 않고 바로 함수명으로 함수 호출 가능
  ```

  ```python
  ## 모듈 내 모든 함수 import
  --------------------------<코드>-----------------------------
  
  from image.io_file.imgread import * 	# 모듈 내 모든 함수를 import
  
  pngread()		# 모듈명.함수명 하지 않고 바로 함수명으로 함수 호출 가능
  jpgread()
  ```

  ```python
  ## 모듈 내 함수 별명 붙여서 호출
  --------------------------<코드>-----------------------------
  
  from image.io_file.imgread import pngread as pre	# pngread()함수를 pre로 간단히 표현
  from image.io_file.imgread import jpgread as jre	# jpgread()함수를 jre로 간단히 표현
  
  pre()
  jre()
  ```

  
