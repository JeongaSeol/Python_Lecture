# Python CH.07 Function

> 특정 기능을 수행하는 코드의 묶음을 함수라고 함
>
> 함수의 입력값을 __인자(Arguments)__라고 하고 함수에서 수행된 결과값을 __반환값(return)__이라고 함
>
> 함수에 따라서 인자와 return값이 없을 수 있음



## 7.1 함수 정의 및 구조

- #### 함수 정의

  `def 함수명(인자1, 인자2, ..., 인자 n) :`

  ​		`<code block>`

  ​		`return 반환값`

  - 함수를 이용하기 위해서는 먼저 정의를 해야함 
  - 함수를 정의한 후 함수를 호출해서 기능을 수행함
  - `함수명`은 주로 영문 알파벳 소문자와 밑줄`_`을 이용
  - 인자는 0개 이상 가능하고 인자는 괄호`( )`를 이용해서 묶어줌. 인자는 콤마`,`로 구분
  - return값이 없으면 입력하지 않으면 됨

- #### 함수의 기본구조

  1. 인자(argument), 반환값(return) 모두 없는 함수
  2. argument는 있으나 return값이 없는 함수
  3. argument와 return값이 모두 있는 함수

- #### 함수 호출

  `함수명(인자1, 인자2, ... , 인자n)` 

  - 함수를 호출할 때는 함수를 정의했을 때 지정했던 인자도 함께 써야함
  - 인자의 개수와 순서는 같아야하고, 인자가 없다면 괄호`()`안에 아무것도 입력하지 않으면 됨
  - 정의만 해서는 아무 작업도 수행이 안됨. 함수를 실행하기 위해선 호출하는 과정이 필요함

  ```python
  def my_func() :
      print("my first function!")		
      print('this is a function.')	# print하는 함수를 정의
  
  my_func()		# 함수 호출
  
    - my first function!
  	this is a function.
  ```

  ```python
  ## argument는 있고, return값이 없는 함수
  
  def my_friend(friendName) :
  	print("{}는 나의 친구입니다.".format(friendName))
  	
  my_friend("철수")			# 정의한 함수에 argument를 각각 입력해서 호출
  my_friend("영미")
  
    - 철수는 나의 친구입니다.
  	영미는 나의 친구입니다.	
  ```

  - 함수에 argument를 이용하면 인자에 따라 다른 결과를 얻을 수 있음

  ```pythonr
  def my_student_info(name, school_ID, phoneNumber) :
  	print("--------------------")
  	print("- 학생 이름: ", name)
  	print("- 학급 번호: ", school_ID)
  	print("- 전화 번호: ", phoneNumber)
  	
  my_student_info("현아", "01", "01-123-4567")
  my_student_info("진수", '02', '02-345-6789')
  
  --------------------
  - 학생 이름:  현아
  - 학급 번호:  01
  - 전화 번호:  01-123-4567
  --------------------
  - 학생 이름:  진수
  - 학급 번호:  02
  - 전화 번호:  02-345-6789 
  ```

  ```python
  ## argument는 있고, return값도 있는 함수
  
  def my_calc(x,y) :
  	z = x*y
  	return z
  	
  my_calc(3,4)
  
    - 12
  ```

  - python에서 함수의 인자로 list, tuple, set, dictionary도 사용 가능

  ```
  ## list를 인자로 갖는 함수
  
  ```

  

  

