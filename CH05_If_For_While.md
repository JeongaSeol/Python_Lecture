# Python CH.05 제어문

## 5.1 If문

> __조건__에 따라 코드를 다르게 실행하기 위해 사용되는 조건문
>
> 지정한 조건에 맞춰 분기해서 명령을 수행
>
> 조건을 만족하는지에 따라 코드 수행 결과가 달라짐

-  `If <조건문> : `

     	 `< code block >`	

  > if 문에서 `<조건문>`을 만족(참)하면  아래의 `<code block>`을 수행하고, 만족하지 않으면 수행안함

   - `< 조건문 >` 다음에는 반드시 __콜론__ `:`을 입력해야함
   - `< code block >`은 탭`Tab`이나 공백(4칸)을 이용해서 반드시 __들여쓰기__ 해야함
      - 들여쓰기가 되어있다면 한 줄 이상의 코드 입력 가능
  - `<조건문>`은 조건의 __True/False__를 판단하기 위해 __비교연산 및 논리 연산__을 이용함
    - 한 개 이상의 비교연산과 논리연산을 조합해서 사용

  ```python
  x = 95
  if x >= 90 :
      print("Pass")
  
   - Pass
  ```



- `If < 조건문 > :`

  ​		`< code block 1 >`

  `else :` 

  ​		`< code block 2 >`

  > `< 조건문 >`을 만족한다면 `< code block 1 >`을 수행, 만족하지 않으면 `< code block 2 >`를 수행

  	- `else` 다음에도 반드시 __콜론__ `:`을 입력해야함
  	- `< code block 2 >`도  `< code block 1 >`과 같이 __들여쓰기__를 해야함
  	- `else`문은 단독으로는 사용 불가능! 반드시 `if`와 함께 사용해야함

  ```python
  x = 75
  if x>=90 :
      print("Pass")
  else :
      print("Fail")
      
  - Fail
  ```



- `If < 조건문 1 > :`

  ​		`< code block 1 >`

  `elif < 조건문 2 > : `

  ​		`< code block 2 >`

  `elif < 조건문 3 > :`

  ​		`< code block 3 >`

  ...

  `else :`

  ​		`<code block n >`

  > 우선 `<조건문1>`을 검사하고 만족하면 `<code block1>`을 수행
  >
  > `<조건문1>`을 만족하지 않으면 `<조건문2>`로 넘어가서 검사 후 만족하면 `<code block2>`를 수행
  >
  > `<조건문2>`를 만족하지 않으면 그 다음 `<조건문>`을 검사하고 해당 `<code block>`을 수행
  >
  > 마지막 `<조건문>`까지 만족하지 않으면 `else`문의 `<code block>`을 수행 

   - 2개 이상의 조건으로 코드 수행을 나누고 싶다면 `elif` 문을 사용
   - `elif`는 필요에 따라 여러 개 사용 가능
   - 만족하는 `<조건문>`의 `<code block>`을 수행했다면 그 아래의 `<조건문>`은 더이상 검사하지 않음
   - `else : `는 생략하고 `if ~ elif ~`만 사용 가능

  ```python
  x = 85
  if x>=90:
      print("very good")
  elif 80 <= x < 90 :
      print("Good")
  else :
      print("Bad")
  
   - Good
  ```

  

- `If < 조건문 1 > :`

  ​		`If < 조건문 1-1 > :`

  ​				`< code block 1-1 >`

  ​		`else :`

  ​				`< code block 1-2 >`

  `elif < 조건문 2 > :`

  ​		`< code block 2 >`

  `else :`

  ​		`< code block 3 >`

  > `<조건문1>`을 만족하면 다시 <조건문1-1>을 검사해서 만족하면 `<code block1-1>` 수행
  >
  > 만족하지 않으면 `<code block1-2>`를 수행
  >
  > `<조건문1>`을 만족하지 않으면 `<조건문2>`를 검사하고, 만족하면 `<code block2>`를 수행
  >
  > 만족하지 않으면 `<code block3>`을 수행

  - `if`문에 `if~else`조건문을 사용한다고 하면 들여쓰기를 해야함
  - 중첩 조건문은 2개 이상 사용 가능

  ```python
  x = 100
  if x >= 90 :
      if x ==100 :
          print("Perfect")
      else :
          print("very Good")
  elif 80 <= x < 90 :
      print("good")
  else :
      print("Bad")
      
   - Perfect
  ```



## 5.2 For문

> 구현한 코드를 원하는 횟수만큼 반복해서 수행하기 위해 사용하는 반복문
>
> 물리적으로 코드를 반복해서 작성하는 것이 아니기 때문에 효율적으로 코딩 구현

- `for <반복 변수> in <반복 범위> :`

  ​		`<code block>`

  > `<반복 변수>`는 `<반복 범위>`에 따라 변하면서 `<code block>`을 실행
  >
  > `<반복 범위>`의 첫 번째 데이터가 `<반복 변수>`에 들어가서 `<code block>`을 실행
  >
  > 그 후 다시 `<반복 범위>`의 두 번째 데이터가 `<반복 변수>`에 들어가서 또 `<code block>`을 실행
  >
  > 이 과정을 `<반복 범위>` 마지막까지 반복해서 실행

  - `<code block>`에서 `<반복 변수>`를 이용할 수 있음
  - `for`문에서도 `<반복 범위>` 다음에 콜론 `:`을 반드시 입력
  - `<code block>`은 `if`문과 마찬가지로 4칸 공백 혹은 탭`Tab`을 이용해서 들여쓰기해야함
  - `<반복 범위>`에 `list`를 사용 가능 

  ```python
  for a in [0,1,2,3,4,5] :		# 반복범위에 리스트사용
      print(a)
  
   - 0
     1
     2
     3
     4
     5
  
  myFriends = ['James', 'Robert', 'Lisa', 'Mary']	# 반복변수와 범위 모두 문자열도 가능
  for friend in myFriends :
       print(friend)
       
   - James
     Robert
     Lisa
     Mary
  ```

- `range(start, stop, step)` : 범위를 반환하는 함수

  - `start`: 범위의 시작 지점.   (양의 정수, 음의 정수, 0 가능)

  - `stop` : 범위의 끝 지점.  __반복 범위에 포함되지는 않음__ (양의 정수, 음의 정수, 0 가능)

  - `step` : 범위 증감의 크기. (양의 정수, 음의 정수만 가능)
  - `start`부터 시작해서 `step`만큼 증감되어 `stop`까지의 반복 범위를 return

  ```python
  print(range(0,10,1))	# range()함수로 만들어진 숫자의 list를 출력하려면 별도로 list()사용
  
   - range(0, 10)
      
  print(list(range(0,10,1))) # list()는 range()함수에 범위의 원소들을 list형식으로 보여줌
   
   - [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
  ```

- `for <반복 변수> in range(start, stop, step) : `

  ​		`<code block>`

  > `<반복범위>`를 list로 값을 직접 지정해도 되지만  range()함수를 이용하여 `<반복범위>`를 지정 가능
  >
  >  `step`은 default로 1.  생략 가능
  >
  > `start`는 default로 0. 생략 가능

  ```python
  for a in range(0,6,2) : 	# start 0부터 step이 2이므로 0,2,4이 순서대로 a에 들어감
      print(a)				# 0,2,4 3번 반복해서 그때마다 a를 출력
  
   - 0
     2
     4
  
  for a in range(5) :		# start값 0, step값이 1일때는 생략 가능 => stop값만 5로 지정
      print(a)
  
   - 0
     1
     2
     3
     4
  ```

- `for <반복변수1> in <반복범위1> :`

  ​		`for <반복변수2> in <반복범위2> :`

  ​				`<code block>`

  >`중첩for문`에서 `<반복변수1>`의 첫 번째 데이터가 실행될 때 그 안에 있는 `for문`을 만나 다시 내부의 
  >
  >`for문`의 `<반복변수2>`가 `<반복범위2>`를 모두 돌 때까지 반복하고, 
  >
  >다시 `<반복변수1>`의 두 번째 데이터가 실행될 때, 또 내부의 `for문`이 반복적으로 수행됨
  >
  >이런 과정을 모두 거쳐서 첫 번째 `for문`이 끝나면 코드가 끝남

  - `중첩for문`에서 `내부for문`과 `<code block>`은 각각 들여쓰기를 해야함

  ```python
  # 코드 설명 : 리스트 변수x,y에 각각 ['x1', 'x2'], ['y1', 'y2']를 할당하고 
  #			 이중for문을 이용해 각 요소로 이루어진 (x, y) 순서쌍을 출력
  
  x_list = ['x1', 'x2']
  y_list = ['y1', 'y2']
  
  for x in x_list :
  	for y in y_list :
  		print('(',x, " ", y, ')' )
  
   - ( x1   y1 )
     ( x1   y2 )
     ( x2   y1 )
     ( x2   y2 )
  ```

- `len(list, tuple, set, dictionary명)` : list, tuple, set, dictionary의 항목 개수('데이터 길이') 반환

  ```python
  a = [1,2,3,4,5,6,7,8,9,10]	# list
  b = (1,2,3,4,5)		# tuple
  c = {'james', 'mary', 'thor', 'ironman', 'captain', 'steve'}	# set
  d = {'Eng':'Lon', 'Ame':'Was', 'Kor':'Seo', 'Jap':'Tok'}	# dict
  
  print(len(a))	# list의 길이
  print(len(b))	# typle의 길이
  print(len(c))	# set의 길이
  print(len(d))	# dictionary의 길이
  
   - 10
     5
     6
     4
  ```

- `zip(A, B)` : 같은 길이의 list A, B의 데이터를 하나로 묶어서 return

  -  for문의 `<반복범위>`에 `zip()`함수를 이용하여 각각의 묶여진 데이터별로 `<반복 변수>`에 지정 가능

  `for var1, var2 in zip(list1, list2) :`

  ​		`<code block>`

  > `<반복 범위>`인 zip()안에 있는 list1, list2의 항목이 각각 순서대로 동시에
  >
  > `<반복 변수>`인 var1, var2에 대입되어 `<code block>`을 수행

  - for문에서 길이가 같은 여러 개의 리스트를 동시에 처리할 때 효율적
  - 좀 더 알아 보기 쉽게 코드를 작성 가능

  ```python
  subj = ['수학', '국어', '영어', '사회', '과학']
  score = [100, 95, 95, 80, 95]
  
  for v1, v2 in zip(subj, score) :	# 수학,100 / 국어,95 이런식으로 두 데이터가 묶여서 
      print(v1, ' : ', v2)			# 각각 v1, v2에 값이 대입됨
      
   - 수학  :  100
     국어  :  95
     영어  :  95
     사회  :  80
     과학  :  95
  ```



## 5.3 while문

> 반복 범위를 직접 지정하는 for문과는 달리 __주어진 조건을 만족할 때까지 작업을 반복__하는 반복문
>
> `<조건문>`에 따라 반복 여부를 결정

- `while < 조건문 > :`

  ​		`< code block>` 

  > `while`문에서 `<조건문>`을 만족하면 `<code block>`을 계속 수행하고
  >
  > `<조건문>`을 만족하지 않으면 더 이상 `<code block>`을 실행하지 않고 `while`문을 빠져나옴

  - `<조건문>` 다음에는 반드시 콜론`:`을 써야함
  - `<code block>`은 반드시 탭`Tab`이나 공백(4칸)을 이용해서 들여쓰기해야함

  - 조건문을 무한으로 반복하지 않도록 `<code block>`에서 조건문을 제어하는 내용의 코드가 있어야함

- `while True :`

  ​		`<code block>` 

  > `<조건문>`자리가 `True`이므로 조건을 항상 만족하는 것과 같아 `<code block>`을 무한 반복함

  - `<code block>`을 무조건 계속 반복하라고 명령을 내려야 할 상황에서 사용
  - 무한 반복하므로 주의해서 다루어야 할 필요가 있음
  - 반복문을 제어하는 `break`와 `continue`와 함께 사용하는 경우가 대부분임 (추후 다룸)

  ```python
  # 코드 설명 : 1부터 차례대로 더해나가다가 sum이 20이상이 되면 코드종료
  #			더해질 때마다 그때의 sum을 출력
  
  i = 0
  sum = 0
  while(sum<20) :
  	i += 1
  	sum += i
  	print("i = ",i, ' / sum = ',sum)
  	
   - i =  1  / sum =  1
     i =  2  / sum =  3
     i =  3  / sum =  6
     i =  4  / sum =  10
     i =  5  / sum =  15
     i =  6  / sum =  21		# sum이 15인 상황에서 조건문을 통과. 그 후 sum이 20을 넘어서 종료
  ```

  

