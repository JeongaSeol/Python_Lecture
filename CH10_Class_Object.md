# Python CH.10 Class & Object



## 10.1 객체(Object) & 클래스(Class) 

- #### 객체

  - __속성__(상태, 특징)과 __행위__(행동, 동작, 기능)로 구성된 대상
  - 주로 현실 세계를 반영하여 사물, 사람, 동물이나 어떤 개념일 수 있음
  - 객체의 특징인 속성은 __변수__로, 객체가 할 수 있는 기능인 행동은 __함수__로 구현
  - 즉, __변수와 함수의 묶음__
    - 예를 들어 사람이라면 이름, 키, 몸무게와 같은 속성은 변수로 구현
    - '걷다', '뛰다', '앉다'와 같은 행동은 함수로 구현
    - 자전거 객체라면 바퀴의 크기, 색깔 등의 속성은 변수로 구현
    - '전진', '방향전환', '정지' 등의 동작은 함수로 구현
  - 객체를 만들고 이용할 수 있는 기능을 제공하는 프로그래밍 언어를 
    __객체지향 프로그래밍(Object-Oriented Programming, OOP) 언어__ / __객체지향 언어__라고 함

- #### 클래스

  - 객체의 공통된 속성과 행위를 __변수와 함수로 정의한 것__
  - 객체를 만들기 위해선 먼저 클래스를 선언해야함
  - 객체는 클래스에서 생성하므로 객체를 __클래스의 인스턴스(Instance)__라고 함
  - 클래스(상위개념) - 객체(하위개념)
  
- #### 클래스 / 객체를 생성하는 이유

  - 규모가 큰 프로그램을 만들 때 유사한 객체가 많이 필요한 경우가 있음
    - 게임의 캐릭터와 같이 비슷한 역할과 속성을 가지는 객체들이 개별적으로 생성하는 것보다 
      공통된 속성과 행위들을 묶어서 클래스로 한번에 관리하는 것이 효율적
    - 객체가 아무리 늘어나도 변수나 함수를 그 때마다 추가로 구현할 필요가 없음



## 10.2 클래스 선언 & 객체 생성

```python
## 클래스 선언
--------------------------<코드>-----------------------------
class 클래스명 :
	[변수1]
	[변수2]			# 클래스 변수 선언
	...
	[변수N]
	
	def 함수1(self[, 인자1, 인자2, ... , 인자n]) :
		< code block >
	
	def 함수2(self[, 인자1, 인자2, ... , 인자n]) :		# 클래스 함수 정의
		< code block >
	
	...
	
	def 함수N(self[, 인자1, 인자2, ... , 인자n]) :
		< code block >
```

- #### 클래스 선언

  - `class` 다음 클래스명, 콜론`:` 을 순서대로 입력

  - 클래스 이름은 보통 알파벳 __대문자로 시작__하는 단어를 연결해 가독성을 높임

  - 클래스 내에서 변수를 선언하고, `def 함수() :` 형식으로 함수를 정의

  - `class 클래스명:` 다음 줄부터는 __들여쓰기__해야함

  - 클래스에서 정의한 함수의 첫 번째 인자는 __self__

    - self는 객체 생성 후에 자신을 참조하는데 이용
    - 대괄호`[]`안에 있는 인자는 필요한 만큼( 0개 이상 ) 사용 가능

  - #### 실습 

    - 자전거 클래스 생성
    - 클래스를 만들기 전에 자전거가 갖는 속성과 동작을 정의 
    - 자전거의 속성 : 바퀴 크기(wheel_size), 색상(color)
    - 자전거의 동작 : 지정된 속도로 이동(move), 좌/우회전(turn), 정지(stop)
    - 자전거 클래스를 선언하고 객체를 생성한 후 클래스에 변수와 함수를 추가해서 클래스를 완성

  ```python
  ## 자전거 클래스 선언
  ## 클래스를 단순화하기 위해서 클래스명이 Bicycle인 자전거 클래스의 원형만 선언
  ## 클래스명(Bicycle)만 있고, 코드부분은 pass로 실제 아무 코드도 작성하지 않음
  --------------------------<코드>-----------------------------
  class Bicycle :	# 클래스 선언
      pass
  					# 변수도, 함수도 없는 클래스
  ```

- #### 객체 생성 및 활용

  - `객체명 = class명() ` : 선언된 class로부터 class의 instance인 객체를 생성
    - class명()의 class는 앞에서 __미리 선언되어__ 있어야함
    - 객체명은 변수명을 만드는 규칙과 같음

  ```python
  ## 정의한 Bicycle 클래스의 객체를 생성
  --------------------------<코드>-----------------------------
  
  my_bicycle = Bicycle()
  
  my_bicycle		# 아직은 어떤 작업도 수행할 수 없지만 Bicycle 클래스의 인스턴스
  
  --------------------------<결과>-----------------------------
  <__main__.Bicycle at 0x7f43a25a6d90>	# 객체를 실행하면 생성 시 할당받은 메모리 주소값 출력
  ```

  - `객체명.변수명 = 속성값` : 객체에 속성을 설정하고 `속성값`을 할당
  - `객체명.변수명` : 객체의 속성값을 출력

  ```python
  ## my_bicycle의 속성값을 할당
  --------------------------<코드>-----------------------------
  
  my_bicycle.wheel_size = 26		# 속성값 정의
  my_bicycle.color = 'black'
  
  print('wheel size = ', my_bicycle.wheel_size)	# 속성값 출력
  print('color = ', my_bicycle.color)
  
  --------------------------<결과>-----------------------------
  wheel size =  26
  color =  black
  ```

  ```python
  ## 선언한 Bicycle 클래스에 함수를 추가
  --------------------------<코드>-----------------------------
  
  class Bicycle :
  	
  	def move(self, speed) :
  		print("자전거 : 시속 {0}km로 전진".format(speed))
  	
  	def turn(self, direction) :
  		print('자전거 : {0}회전'.format(direction))
  		
  	def stop(self) :
  		print("자전거({0}, {1}): 정지".format(self.wheel_size, self.color))
          	# 객체의 바퀴크기, 색깔 속성값을 가져와서 출력
              
  ```
  
  - 객체의 메서드 호출할 때
    - `객체명.메서드명([인자1, 인자2, ... , 인자n])` 
    - 메서드 : 클래스에서 정의한 함수
    - `인자`는 클래스에서 정의한 함수의 인자만큼 필요(개수가 일치해야함)
    - 클래스에서 선언할 때 추가했던 함수의 인자 __self는 필요하지 않음__
      - self만 인자로  갖도록 정의한 함수를 객체에서 이용할 때는 소괄호에 인자를 지정하지 않음
  
  ```python
  ## 구현한 Bicycle 클래스에서 객체를 생성한 후 속성을 설정하고 객체의 메서드를 호출
  --------------------------<코드>-----------------------------
  
  class Bicycle:
  	
  	def move(self, speed) :
  		print("자전거 : 시속 {0}km로 전진".format(speed))
  	
  	def turn(self, direction) :
  		print('자전거 : {0}회전'.format(direction))
  		
  	def stop(self) :
  		print("자전거({0}, {1}): 정지".format(self.wheel_size, self.color))
  
  my_bicycle = Bicycle()		# Bicycle 클래스의 인스턴스인 my_bicycle 객체 생성
  
  my_bicycle.wheel_size = 26	# 객체의 속성 설정
  my_bicycle.color = 'black'
  
  my_bicycle.move(30)		# 객체의 메서드 호출
  my_bicycle.turn('좌')
  my_bicycle.stop()		# self 인자는 호출시에는 채우지 않음
  
  --------------------------<결과>-----------------------------
  자전거 : 시속 30km로 전진
  자전거 : 좌회전
  자전거(26, black) : 정지
  ```
  
  ```python
  ## 2개의 객체 생성 및 활용
  --------------------------<코드>-----------------------------
  
  class Bicycle:
  	
  	def move(self, speed) :
  		print("자전거 : 시속 {0}km로 전진".format(speed))
  	
  	def turn(self, direction) :
  		print('자전거 : {0}회전'.format(direction))
  		
  	def stop(self) :
  		print("자전거({0}, {1}): 정지".format(self.wheel_size, self.color))
  
  bicycle1 = Bicycle()
  
  bicycle1.wheel_size = 27
  bicycle1.color = 'red'
  
  bicycle1.move(20)
  bicycle1.turn('좌')
  bicycle1.stop()
  
  bicycle2 = Bicycle()
  bicycle2.wheel_size = 24
  bicycle2.color = 'blue'
  
  bicycle2.move(15)
  bicycle2.turn('우')
  bicycle2.stop()
  
  --------------------------<결과>-----------------------------
  자전거 : 시속 20km로 전진
  자전거 : 좌회전
  자전거(27, red): 정지
  자전거 : 시속 15km로 전진
  자전거 : 우회전
  자전거(24, blue): 정지
  ```
  
- #### 객체 초기화

  > 지금까지는 Bicycle 클래스를 선언하고, 객체를 생성한 후에 객체의 속성을 설정
  >
  > 클래스를 선언할 때 초기화 함수를 구현하여 객체를 생성하는 것과 동시에 속성값들을 지정 할 수 있음

  - `__init__()` : 클래스의 인스턴스가 생성(객체가 생성)될 때 자동으로 실행해서 __객체의 속성을 초기화__
    - `__init__(self, wheel_size, color)` 함수는 wheel_size, color를 인자로 입력받아 함수 내에서
      `self.변수명 = 인자`로 객체의 속성을 초기화
    - 객체를 생성할 때 `__init__()`함수의 인자를 입력(self는 제외)함
    - `객체명 = 클래스명(인자1, 인자2, ... , 인자n)
    - 객체를 생성한 후 속성값을 따로 지정할 필요 없이 객체 생성과 동시에 속성값이 할당됨

  ```python
  ## Bicycle 클래스에 초기화함수 __init__() 함수 추가 후 객체 생성
  --------------------------<코드>-----------------------------
  
  class Bicycle:
      
      def __init__(self, wheel_size, color):
          self.wheel_size = wheel_size
          self.color = color
          
      def move(self, speed) :
          print("자전거가 {0}km/h로 전진합니다.".format(speed))
         
      def turn(self, direction) :
          print("자전거가 {0}회전 합니다.".format(direction))
          
      def stop(self) :
          print("자전거({0},{1})가 정지합니다.".format(self.wheel_size, self.color))
          
  my_bicycle = Bicycle(26, 'black')
  
  my_bicycle.move(30)
  my_bicycle.turn('좌')
  my_bicycle.stop()
  
  --------------------------<결과>-----------------------------
  자전거가 30km/h로 전진합니다.
  자전거가 좌회전 합니다.
  자전거(26,black)가 정지합니다.
  ```



## 10.3 클래스를 구성하는 변수와 메서드(함수)

- #### 클래스에서 사용하는 변수

  - 위치에 따라 __클래스 변수__(class variable), __인스턴스 변수__(instance variable)로 구분

  - #### 클래스 변수(class variable)

    -  클래스 내에 있지만 메서드 밖에서 `변수명 = 데이터` 형식으로 정의한 변수
    - `클래스명.변수` 또는 `객체명.변수`로 접근 할 수 있음
    - 클래스에서 생성한 __모든 객체가 공통으로 사용__

  - #### 인스턴스 변수(instance variable)

    - 클래스 내의 메서드 안에서 `self.변수명 = 데이터`형식으로 정의한 변수
    - 클래스 내의 모든 함수에서 `self.변수명`으로 접근 할 수 있음
    - __각 인스턴스(객체)에서 개별적으로 사용__

  - 클래스 변수와 인스턴스 변수는 이름이 같더라도 별개로 동작

  ```python
  ## 클래스 변수와 인스턴스 변수를 사용한 자동차 클래스
  --------------------------<코드>-----------------------------
  
  class Car :
  	
  	instance_count = 0		# 클래스 변수
  	
  	def __init__(self, size, color) :
  		self.size = size		# 인스턴스 변수
  		self.color = color		# 인스턴스 변수
  		Car.instance_count += 1
  		print('자동차 객체의 수 : {0}'.format(Car.instance_count))
  		
  	def move(self) :
  		print('자동차({0}, {1}) 이동.'.format(self.size, self.color))
          
          
  car1 = Car('small', 'white')
  car2 = Car('big', 'black')
  
  --------------------------<결과>-----------------------------
  자동차 객체의 수 : 1	
  자동차 객체의 수 : 2	# 클래스 변수는 모든 객체가 공통으로 사용하므로 객체 생성시마다 1씩 증가
  ```

  ```python
  ## 클래스 변수는 `클래스명.변수명` 또는 `객체명.변수명`으로 호출 가능 (공통으로 관리)
  --------------------------<코드>-----------------------------
  
  class Car :
  	
  	instance_count = 0		# 클래스 변수
  	
  	def __init__(self, size, color) :
  		self.size = size		# 인스턴스 변수
  		self.color = color		# 인스턴스 변수
  		Car.instance_count += 1
  		print('자동차 객체의 수 : {0}'.format(Car.instance_count))
  		
  	def move(self) :
  		print('자동차({0}, {1}) 이동.'.format(self.size, self.color))
          
          
  car1 = Car('small', 'white')
  car2 = Car('big', 'black')
  
  print('Car 클래스의 총 인스턴스 개수 : ', Car.instance_count)	# `클래스명.변수명`으로 호출
  print('Car 클래스의 총 인스턴스 개수 : ', car1.instance_count)	# `객체명.변수명`으로 호출
  print('Car 클래스의 총 인스턴스 개수 : ', car2.instance_count)
  
  car1.move()
  car2.move()
  
  --------------------------<결과>-----------------------------
  자동차 객체의 수 : 1
  자동차 객체의 수 : 2
  Car 클래스의 총 인스턴스 개수 :  2
  Car 클래스의 총 인스턴스 개수 :  2
  Car 클래스의 총 인스턴스 개수 :  2	# 클래스변수는 공동으로 관리하므로 어느 객체로 호출해도 같은 값
  자동차(small, white) 이동.
  자동차(big, black) 이동.	# 인스턴스변수는 각각의 객체에서 별도로 관리되므로 객체마다 다른 값
  ```

  ```python
  ## 이름이 같은 클래스 변수와 인스턴스 변수
  --------------------------<코드>-----------------------------
  
  class Car2 :
  	count = 0		# 클래스 변수
  	
  	def __init__(self, size, num) :
  		self.size = size
  		self.count = num		# 인스턴스 변수
  		Car2.count = Car2.count +1
  		print('자동차 객체 수 : Car2.count = ', Car2.count)
  		print('인스턴스 변수 초기화 : self.count = ', self.count)
  		
  	def move(self) :
  		print('자동차({0}, {1}) 이동'.format(self.size, self.count))
  		
  car1 = Car2('big', 20)
  car2 = Car2('small', 30)
  
  --------------------------<결과>-----------------------------
  자동차 객체 수 : Car2.count =  1
  인스턴스 변수 초기화 : self.count =  20
  자동차 객체 수 : Car2.count =  2			# 클래스변수는 공통으로 관리
  인스턴스 변수 초기화 : self.count =  30	  # 인스턴스변수는 각 객체마다 관리 
  ```



- #### 클래스에서 사용하는 함수

  - #### 인스턴스 메서드(instance method)

    - __각 객체에서 개별적으로 동작하는 함수__를 만들 때 사용하는 함수
    - 인스턴스 메서드는 정의할 때 첫 인자로 __self__가 필요
    - self는 클래스의 인스턴스(객체) 자신을 가리킴
    - self를 이용하여 인스턴스 변수를 만들고 사용함
    - 인스턴스 메서드 안에서는 `self.함수명()` 형식으로 클래스 내의 다른 함수를 호출 가능
      - 클래스 내의 함수에서 인스턴스 메서드 호출 시 인자에 self는 전달하지 않음
    - 객체를 생성한 후에 `객체명.메서드명([인자1, 인자2, ... , 인자n])`으로 호출

    ```python
    ## 인스턴스 메서드 구조
    --------------------------<코드>-----------------------------
    
    class 클래스명 :
    	
    	def 함수명(self[, 인자1, 인자2, ... , 인자n]) :
    		
    		self.변수명1 = 인자1
    		self.변수명2 = 인자2
    		...
    		self.변수명n = 인자n
    		
    		< code block >
            
    ```

    ```python
    ## 인스턴스 메서드 실습
    --------------------------<코드>-----------------------------
    
    class Car:
    	instance_count = 0	
    	
    	def __init__(self, size, color) :	#인스턴스 메서드(초기화 함수)
    		self.size = size
    		self.color = color
    		Car.instance_count += 1
    		print('자동차 객체의 수 : ', Car.instance_count)
    		
    	def move(self, speed) :		# 인스턴스 메서드
    		self.speed = speed
    		print('자동차({0}, {1})가'.format(self.size, self.color), end='')
    		print('{0}km/h로 전진'.format(self.speed))
    	
    	def auto_cruise(self) :		# 인스턴스 메서드
    		print('자율 주행 모드')
    		self.move(self.speed)	# move()함수의 인자로 인스턴스 변수를 입력
    
    car1 = Car('small', 'red')
    car2 = Car('big', 'green')
    
    car1.move(80)
    car2.move(100)
    
    car1.auto_cruise()
    car2.auto_cruise()	
    			# 인스턴스 메서드인 move()와 auto_cruise()는 각각의 객체에서 개별적으로 동작
    							
    --------------------------<결과>-----------------------------
    자동차 객체의 수 :  1
    자동차 객체의 수 :  2
    자동차(small, red)가80km/h로 전진
    자동차(big, green)가100km/h로 전진
    자율 주행 모드
    자동차(small, red)가80km/h로 전진
    자율 주행 모드
    자동차(big, green)가100km/h로 전진
    ```

     

  - #### 정적 메서드(static method)

    -  클래스와 관련이 있어서 클래스 안에서 정의되기는 하지만 클래스나 클래스의 인스턴스(객체)와는 무관하게 독립적으로 동작하는 함수를 만들 때 사용하는 함수
      - 날짜 및 시간 정보, 환율 정보 제공, 단위 변환과 같이 객체와 독립적으로 동작
    - 인자로 self를 사용하지 않고, 정적  메서드 안에서는 인스턴스 메서드 / 인스턴스 변수에 접근 불가
    - 함수 앞에 데코레이터`@staticmethod`를 선언해 정적 메서드임을 표시

    ```python
    ## 정적 메서드의 구조
    --------------------------<코드>-----------------------------
    
    class 클래스명:
    	
    	@staticmethod
        def 함수명([인자1, 인자2, ... , 인자n]) :		# self인자 없음
        	<code block>
    ```

    - 객체를 생성한 후에 정적 메서드를 호출할 수도 있지만 보통 객체를 생성하지 않고 
      클래스명을 이용해 바로 메서드를 호출 
    - `클래스명.메서드명([인자1, 인자2, ... , 인자n])`으로 호출

    ```python
    ## 앞서 만든 Car클래스에 정적 메서드인 check_type()을 추가
    --------------------------<코드>-----------------------------
    
    class Car:
    	instance_count = 0	
    
    	# 앞에서 사용한 인스턴스 메서드 그대로 사용
    	def __init__(self, size, color) :	#인스턴스 메서드(초기화 함수)
    		self.size = size
    		self.color = color
    		Car.instance_count += 1
    		print('자동차 객체의 수 : ', Car.instance_count)
    		
    	def move(self, speed) :		# 인스턴스 메서드
    		self.speed = speed
    		print('자동차({0}, {1})가'.format(self.size, self.color), end='')
    		print('{0}km/h로 전진'.format(self.speed))
    	
    	def auto_cruise(self) :		# 인스턴스 메서드
    		print('자율 주행 모드')
    		self.move(self.speed)	
    		
    	@staticmethod		# 정적메서드 정의
    	def check_type(model_code):				# self 인자 없음
    		if(model_code >= 20):
    			print('이 자동차는 전기차입니다.')
    		elif(10 <= model_code < 20) :
    			print('이 자동차는 가솔린차입니다.')
    		else:
    			print('이 자동차는 디젤차입니다.')
    			
    Car.check_type(25)
    Car.check_type(2)		# 객체를 생성하지 않고 보통 클래스명.메서드명으로 호출
    
    --------------------------<결과>-----------------------------
    이 자동차는 전기차입니다.
    이 자동차는 디젤차입니다.
    ```

     

  - #### 클래스 메서드(class method)

    - 클래스 변수를 사용하기 위한 함수
      - 생성된 객체의 개수를 반환하는 등 클래스 전체에서 관리해야 할 기능이 있을 때 주로 이용
    - 함수를 정의할 때 __첫 번째 인자로 클래스를 넘겨받는 `cls`가 필요__
      - 이를 이용하여 클래스 변수에 접근 
      - `cls.변수명` 으로 클래스 변수에 접근가능
    - 클래스 메서드를 사용하기 위해서 함수 앞에 데코레이터 `@classmethod`를 지정

    ```
    ## 클래스 메서드의 구조
    --------------------------<코드>-----------------------------
    
    class 클래스명 :
    	
    	@classmethod
    	def 함수명(cls[, 인자1, 인자2, ... , 인자n]):
    		< code block >
    ```

    - 객체를 생성하지 않고 클래스명을 이용하여 바로 호출 
      - `클래스명.메서드명([인자1, 인자2, ... , 인자n])`

    ```python
    ## 앞서 정의한 Car 클래스에서 클래스 메서드인 count_instance()를 추가
    --------------------------<코드>-----------------------------
    
    class Car:
    	instance_count = 0	
    
    	# 앞에서 사용한 인스턴스 메서드 그대로 사용
    	def __init__(self, size, color) :	#인스턴스 메서드(초기화 함수)
    		self.size = size
    		self.color = color
    		Car.instance_count += 1
    		
    	def move(self, speed) :		# 인스턴스 메서드
    		self.speed = speed
    		print('자동차({0}, {1})가'.format(self.size, self.color), end='')
    		print('{0}km/h로 전진'.format(self.speed))
    	
    	def auto_cruise(self) :		# 인스턴스 메서드
    		print('자율 주행 모드')
    		self.move(self.speed)	
    		
    	@staticmethod		# 정적메서드 정의
    	def check_type(model_code):				# self 인자 없음
    		if(model_code >= 20):
    			print('이 자동차는 전기차입니다.')
    		elif(10 <= model_code < 20) :
    			print('이 자동차는 가솔린차입니다.')
    		else:
    			print('이 자동차는 디젤차입니다.')
    			
    	@classmethod
    	def count_instance(cls):
    		print('자동차 객체의 개수 ', cls.instance_count)
    
    Car.count_instance()		# 객체 생성 전 클래스 메서드 호출
    car1 = Car('small', 'red')	# 객체1 생성
    Car.count_instance()		# 객체1 생성 후 클래스 메서드 호출
    
    car2 = Car('big', 'green')	# 객체2 생성
    Car.count_instance()		# 객체2 생성 후 클래스 메서드 호출
    
    --------------------------<결과>-----------------------------
    자동차 객체의 개수  0
    자동차 객체의 개수  1
    자동차 객체의 개수  2	# 객체를 생성할 때마다 클래스 변수인 instance_count의 값이 1씩 증가
    ```

