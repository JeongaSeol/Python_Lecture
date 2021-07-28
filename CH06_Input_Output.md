# Python CH.06 Input / Output

> 코딩을 실행한 결과를 화면이나 파일로 출력할 때
>
> 키보드로 입력 데이터를 받거나, 파일에 있는 데이터를 읽어서 처리할 때
>
> Python으로 코드를 작성할 때 키보드와 화면으로 입출력하는 방법 & 파일로 입출력하는 방법을 배움



## 6.1 화면 출력

- `print()` : 원하는 내용을 화면으로 출력

  - `print("원하는 문자열")` : 문자열을 출력할 때는 `" "`나 `' '`로 묶어줌
    - 문자열을 여러 개 연결해서 출력하기 위해 콤마(`,`)를 사용함. 출력시 빈칸(공백)이 한칸씩 들어감
    - `sep = 문자열` : `print()` 함수 안 문자열 사이의 구분하는 값을 빈칸 대신 다른 문자열로 설정
    - `+` : 콤마(`,`)대신 사용시 빈칸 없이 문자열끼리 연결해서 출력

  ```python
  print("Best", "python", "book") 	# 세 개의 문자열 사이 공백과 함께 연결되어 출력
  
   - Best python book
  ```

  ```python
  print("Best", "python", 'book', sep = "-:*:-") 	# 문자열 사이 공백 대신 -:*:- 문자열 삽입
  
   - Best-:*:-python-:*:-book
  ```

  ```python
  print('abcd' + 'efg')		# 공백 없이 두 문자열을 연결시키기 위해서는 + 연산자 이용
  
   - abcdefg
  ```

  ```python
  print("best", "python", "book" + ":", 'This book')		# 콤마와 +연산 혼합해서 사용 가능
  
   - best python book: This book
  ```

  - `print(변수명)` : 문자열 뿐만 아니라 변수를 인자로 입력하면 변수 값이 출력됨
    - 변수를 출력할 때는 변수명을 따옴표(`" "`) 없이 입력해야함
    - 문자열과 함께 출력하기 위해서는 콤마(`,`)로 구분해서 입력해줌
    - __문자열과 숫자는 + 연산자로 연결 불가능__

  ```python
  x = 10					# 변수명을 인자로 입력하면(따옴표 없이) 변수값이 출력됨
  print(x)
  
   - 10
  
  y = [1,2,3]
  print(y)
  
   - [1, 2, 3]
  
  z = ('a', 'b', 'c')
  print(z)	
   
    - ('a', 'b', 'c')
  ```

  ```python
  name = "James"
  ID_num = 789
  print("Name:", name + ",", "ID Number:", ID_num)	# 문자열과 숫자는 +연산자로 연결 불가
  
   - Name: James, ID Number: 789
  ```

  - `\n` : `print()`은 출력시 한줄씩 출력됨. 문자열 안에 개행문자 `\n`을 입력 시 출력할 때 줄바꿈 가능

  ```python
  print("James is my friend. \nHe is Korean")	# 개행문자 사용하여 하나의 print()함수에 
  											# 한 줄 이상의 문자열을 출력 가능
   - James is my friend. 
     He is Korean
  ```

  ```python
  print("James is my friend. \n\nHe is Korean")	# 개행문자 사용하여 한 줄 띄우기 가능
  
   - James is my friend. 
  
     He is Korean
  ```

  - `end = "문자열"` : print() 출력 라인 끝의 값을 지정할 수 있음
    - `end`를 지정하지 않으면 기본적으로 `print()`출력 결과 라인 끝에는 개행문자(`\n`)이 들어감
    - 개행문자(`\n`) 대신 다른 문자열을 입력하려면 `end = "문자열"` 형태로 다른 값을 입력

  ```python
  print("welcome to", end = " ")		# 출력 라인 마지막에 개행이 아닌 공백을 입력
  print("python!")
  
   - welcome to python!			# 문자열('python!')이 그다음 줄이 아닌 공백 다음에 출력
  ```

  ```python
  print("welcome to python", end = "!!!!!" )	# 출력 라인 마지막 값을 '!!!!!'로 입력
  
   - welcome to python!!!!!		
  ```

  - `print("%type" %data)` : data의 형식과 위치를 지정해서 출력
    - 출력하고자 하는 문자열 중 data의 위치를 따옴표(`" "`)안에서 `%type`으로 표현
    - __따옴표(`" "`)와 %data 사이__에는 콤마가 아닌 __공백으로 구분__함
    - data가 __문자열이면 `%s`__, __정수면 `%d`(또는 `%i`)__, __실수이면 `%f`(또는 `%F`)__로 지정
    - 실수의 경우 `%f`는 기본적으로 소수점 6자리까지 출력
    - 출력할 data가 두 개 이상일 때는 data 개수에 맞게 `%type`을 순서대로 입력하고 tuple 형식`( )`으로 data를 묶어서 사용함
    - `print("%type %type" % (data1, data2))`

  ```python
  name = "Rose"
  print("%s is my friend!" % name) 	# data(=name)이 문자열이므로 %s를 원하는 위치에 입력
  
   - Rose is my friend!
  ```

  ```python
  r = 3
  pi = 3.1415926665358879
  print("반지름 : %d, 원주율 : %f" % (r, pi))	# 두 개 이상의 data를 위치 지정하여 출력
  
   -  반지름 : 3, 원주율 : 3.141593				# %f는 기본적으로 소수점 6자리까지만 출력
  ```

  - `print("{0} {1} {2} ... {n}".format(data_0, data_1, data_2, ...data_n))` 
    - {n}의 n은 0부터 시작하며 format()에서 data_index를 의미
    - 즉, {n}의 위치에는 format()에서의 data_n의 데이터가 들어가서 출력
    - format() 안의 데이터를 순차적으로 지정하려면 `{ }`만 입력해도 가능
    - 문자열 뿐만 아니라 정수나 실수도 출력 가능
    - 데이터가 숫자인 경우 `{n: 출력형식}`형태로 출력 형식을 지정할 수 있음

  ```python
  animal_0 = 'cat'
  animal_1 = 'dog'
  animal_2 = 'fox'
  
  print("Animal: {0}".format(animal_0))		# 데이터 하나만 위치 지정해서 출력
  print("Animal: {0}, {1}, {2}".format(animal_0, animal_1, animal_2))
  		# 데이터가 animal_0,1,2 순서로 출력
  print("Animal: {1}, {2}, {0}".format(animal_0, animal_1, animal_2))
  		# 데이터가 animal_1,2,0 순서로 출력
  print("Animal: {0}, {1}, {2}".format(animal_2, animal_0, animal_1))
  		# 데이터가 animal_2,0,1 순서로 출력
      
   - Animal: cat
     Animal: cat, dog, fox
     Animal: dog, fox, cat
     Animal: fox, cat, dog
  ```

  ```python
  animal_0 = 'cat'
  animal_1 = 'dog'
  animal_2 = 'fox'
  
  print("Animal: {}, {}, {}".format(animal_0, animal_1, animal_2))
  		# 순차적으로 animal_0,1,2가 출력됨 (유지보수하기에는 적합하지 않음 = 비추천!)
  		
   - Animal: cat, dog, fox
  ```

  ```python
  name = "Tomas"
  age = 19
  a = 0.123456789012346578
  fmt_string = "String: {0}, Integer Number: {1}, Floating Number: {2}"
  		# print()문에 입력할 string을 변수로 따로 지정해서 사용 가능
  print(fmt_string.format(name, age, a))
  		# {0}, {1}, {2}에 차례대로 name(문자열), age(정수), a(실수)이 출력됨
  		
   - String: Tomas, Integer Number: 19, Floating Number: 0.12345678901234658
  ```

  ```python
  a = 0.12345678901234567
  print("{0:.2f}, {0:.5f}".format(a))		# 각각 소수점 둘째자리, 다섯째자리까지 출력
  
   - 0.12, 0.12346
  ```

  - 숫자의 출력 형식 지정

  |   데이터    | 출력 형식 |      출력 결과       |                             설명                             |
  | :---------: | :-------: | :------------------: | :----------------------------------------------------------: |
  |      3      |  {N:2d}   |       (공백)3        |            정수를 공백을 포함해서 두 자리로 표현             |
  |      3      |  {N:05d}  |        00003         |        정수를 다섯자리로 표시. 앞의 공백을 0으로 채움        |
  |     12      |  {N:>5d}  | (공백)(공백)(공백)12 |        정수를 다섯자리로 표시. 숫자는 오른쪽으로 정렬        |
  |   0.12345   |  {N:.3f}  |        0.123         |           실수를 소수점 셋째 자리까지 표시(반올림)           |
  |   746700    |   {N:,}   |       746,700        |              끝에서 셋째자리마다 콤마(,)를 표시              |
  |   0.3257    |  {N:1%}   |        32.6%         | 소수를 퍼센트(%)로 표시. 소수점 자리수는 콜론(:) 다음 숫자로 표시 |
  | 92500000000 |  {N:.2e}  |       9.25e+10       |  숫자를 지수로 표시. 소수점 자리 수는 (:.) 다음 숫자로 표시  |
  |     16      |  {N:#x}   |         0x10         |     숫자를 16진수로 표시. # 기호가 없을 경우 0x없이 출력     |
  |      8      |  {N:#0}   |         0o10         |     숫자를 8진수로 표시. # 기호가 없을 경우 0o없이 출력      |
  |      2      |  {N:#b}   |         0b10         |     숫자를 2진수로 표시. # 기호가 없을 경우 0b없이 출력      |



## 6.2 키보드 입력

- `data변수명 = input("문자열")` : 데이터를 입력받고, 그 값을 처리하는 방법

  - `input()`안의 "문자열"(인자) 부분은 화면에 표시됨
  - 키보드로 데이터를 입력 후 `Enter`를 누르면 입력된 데이터는 __문자열 형태__로 data변수에 대입

  ```python
  yourName = input("이름을 입력하시오 : ")
  print("당신은 {0}이군요.".format(yourName))
  
   - 이름을 입력하시오 : 설정아 `Enter`	# 실행창에서 이름을 입력하고 Enter를 누르면 그 다음이 실행
     당신은 설정아이군요.
  ```

  - `input()`은 문자열로 data를 받기 때문에 만일 숫자를 입력받았다면 출력은 문제가 없지만

    그 숫자를 이용해서 연산에 이용한다면 error 발생

  - `int(문자열)`, `float(문자열)` : 문자열로 된 숫자를 정수형/실수형으로 변환해줌

    - 입력하는 숫자가 정수인지 실수인지 명확하지 않을 경우 `float()`을 사용

  ```python
  num = input("숫자를 입력하세요: ")
  print("당신이 입력한 숫자는 {}입니다.".format(num))
  		# 입력받은 숫자는 문자열 type이지만 출력에는 그대로 사용해도 문제가 없음
  
   - 숫자를 입력하세요: 44 `Enter`
     당신이 입력한 숫자는 44입니다.
  ```

  ```python
  a = input("정사각형 한 변의 길이: ")
  area = int(a) ** 2		# 문자열type의 data(a)를 정수형 변수로 변환해준 후 연산
  print("정사각형의 넓이 : {}".format(area))
  
   - 정사각형 한 변의 길이는: 5 `Enter`
     정사각형의 넓이 : 25
  ```

  ```python
  b = input("정사각형 한 변의 길이 : ")
  area = float(b) ** 2	# 문자열type의 data(b)를 실수형 변수로 변환해준 후 연산
  print("정사각형의 넓이 : {}".format(area))
  
   - 정사각형 한 변의 길이 : 2.5 `Enter`
     정사각형의 넓이 : 6.25
  ```

  

## 6.3 파일 읽고 쓰기

> 출력 결과를 파일로 출력하거나 데이터를 파일에서 읽어야 할 때 
>
> 데이터를 파일로 저장(출력)하는 방법과 데이터가 저장되어 있는 파일에서 데이터를 읽는 방법을 배움



### 파일 열기

- `f = open('파일명', 'mode')`: '파일명'에 해당하는 파일을 열고 파일 객체를 f로 대입 

  - `f`를 이용하여 파일을 읽고 쓰고 닫음

  - `'파일명'` : 읽고 싶은(열고자 하는) 파일 이름

  - `'mode'` : 파일 열기의 속성

    | mode | 의미                                                         |
    | :--: | ------------------------------------------------------------ |
    |  r   | (기본) 읽기 모드로 파일 열기. `'mode'`를 지정하지 않으면 default로 읽기모드가 지정됨 |
    |  w   | 쓰기 모드로 파일 열기.  같은 이름의 파일이 있으면 기존 내용은 모두 삭제됨(overwrite) |
    |  x   | 쓰기 모드로 파일 열기.  같은 이름의 파일이 있으면 오류 발생  |
    |  a   | 추가 모드로 파일 열기. 같은 이름의 파일이 없으면 `w`와 기능이 같음 |
    |  b   | 바이너리 파일 모드로 파일 열기                               |
    |  t   | (기본) 텍스트 파일 모드로 파일 열기. 지정하지 않으면 default로 텍스트 모드로 지정됨 |

  - `mode`는 혼합해서 사용 가능 : ex) 바이너리 파일을 읽기 모드로 열고 싶으면 `mode`에 `bw`/`wb` 입력
  - `mode`를 지정하지 않으면 `rt`와 같은 기능(읽기 모드이면서 텍스트 모드)
  - `w`만 입력시 `wt`모드로 파일을 오픈



### 파일 쓰기

- `f.write(str)`

  `f.close()`		 : 파일에 내용을 쓰고난 후, 파일을 닫음

  - 파일 쓰기를 하기 위해서는 반드시 파일을 __쓰기 모드로 열어야함__
  - 파일을 열고 지정한 내용을 쓴 후에는 반드시 __파일을 닫아야함__
  - 파일을 닫고 나면 파일 객체인 f도 사라짐
  - `f.write(str)`에서 `str`은 기록하고 싶은 내용(문자열)
  - `write()`에서는 `print()`함수에서 사용하는 출력 방식 그대로 이용할 수 있음
    - 따옴표(`" "`/`' '`)를 이용하여 문자열을 파일로 저장(출력)하거나
    - 형식 지정 출력 방식을 이용해 문자열을 파일로 저장(출력) 가능
  - `!cat 파일이름.파일형식` : 해당 파일이 존재하는지 확인 후 있으면 내용을 출력, 없으면 오류 메세지 출력

  ```python
  f = open('myFile.txt','w')				# myFile.txt파일을 쓰기모드로 열기
  f.write("this is my first file.")		# myFile.txt파일에 해당 문자열 내용을 출력(저장)
  f.close()								# write()한 후에는 반드시 close()로 닫기
  !cat myFile.txt							# myFile.txt파일이 있다면 내용출력, 없으면 오류
  
   - this is my first file.
  ```



### 파일 읽기

- `data = f.read()`

  `f.close()` 			:  파일의 내용을 읽어서 data 변수에 대입하고, 마지막으로 파일을 닫음

  - 파일 읽기를 하기 위해서는 반드시 파일을 __읽기 모드로 열어야함__
  - 파일의 내용을 읽고 난 후에는 반드시 __파일을 닫아야함__

  ```python
  f = open('myFile.txt', 'r')			# myFile.txt파일을 읽기모드로 열기
  file_text = f.read()				# myFile.txt파일의 내용을 file_text변수에 대입
  f.close()							# read()한 후에는 반드시 close()로 닫기
  
  print(file_text)					# 파일 내용을 확인하기 위해 file_text를 화면에 출력
  
   - this is my first file.
  ```



### 파일 읽고 쓰기(응용)

- 반복문을 이용해 파일을 읽고 쓰기

  1.  파일 열기(file open)
  2.  반복문을 이용해서 한줄씩 쓰기
  3. 파일 닫기(file close)

  ```python
  ## 구구단 2단 일부를 파일에 출력(저장)하기
  
  f = open("two_times_table.txt",'w')		# 쓰기모드로 파일 열기
  for num in range(1,6):		# 반복문을 통해 2*1에서 2*5까지만 입력
      format_string = "2 * {0} = {1}\n".format(num, 2*num)
      # 파일에 저장할 데이터를 변수에 할당
      f.write(format_string)		# 파일에 쓰기 
  f.close()						# 항상 마지막에 파일 닫기
  !cat two_times_table.txt		# 파일 안의 data를 확인
  
   - 2 * 1 = 2
     2 * 2 = 4
     2 * 3 = 6
     2 * 4 = 8
     2 * 5 = 10
  ```

  ```python
  ## (응용버전) 원하는 단을 입력받아서 해당 구구단을 파일에 출력(저장)하고, 파일 안 data를 확인
  
  f = open("n_times_table.txt",'w')				
  num = int(input("원하시는 단을 입력해주세요 :"))	# 원하는 단 입력받기
  for i in range(1,10) :
      string = "{0} * {1} = {2}\n".format(num, i, num*i)	
      f.write(string)
  f.close()
  !cat n_times_table.txt
  
   - 원하시는 단을 입력해주세요 :8
     8 * 1 = 8
     8 * 2 = 16
     8 * 3 = 24
     8 * 4 = 32
     8 * 5 = 40
     8 * 6 = 48
     8 * 7 = 56
     8 * 8 = 64
     8 * 9 = 72
  ```

- `readline()` : 파일로부터 문자열 한 줄씩 읽음

  - `readline()`을 사용시 그 다음 문자열 한 줄을 read
  - 실행한 횟수만큼 문자열을 한 줄씩 읽음(반복문 이용)
  - 마지막 한 줄을 읽고 나서 다시 `readline()`을 수행하면 빈 문자열을 return

  ```python
  f = open("two_times_table.txt")
  line1 = f.readline()		# txt파일의 첫 번째 줄을 읽음
  line2 = f.readline()		# txt파일의 두 번째 줄을 읽음
  f.close()					# 항상 작업 끝난 후 파일 닫기
  print(line1, end = "")		# 첫번째 줄 출력 - 이미 readlin()에 개행문자(\n)가 포함되어
  print(line2, end = "")		# 있으므로 print()문에서는 end인자를 빈문자열("")로 설정
  ```

  - `while()`문을 이용해서 파일의 전체 데이터를 한 줄씩 읽어오기

  ```python
  f = open("two_times_table.txt")
  line = f.readline()			# 첫 번째 줄 읽기
  while line :				# line이 마지막(빈 문자열)이 아닐 때까지 반복
      print(line, end = "")	# 읽어온 line을 출력. 이미 \n이 포함되어있으므로 end인자 수정
      line = f.readline()		# 다음 line 읽어오기
  f.close() 					# 마지막엔 항상 파일 닫기
  ```

- `readlines()` : 파일 전체의 모든 줄을 읽어서 한 줄 씩을 요소로 갖는 __리스트 타입__으로 return

  - `readlines()`를 받은 리스트의 각 항목에는 파일에서 한 줄 씩 읽은 문자열이 들어있고, `\n`도 포함

  ```python
  f = open("two_times_table.txt")
  lines = f.readlines()			# 파일의 데이터를 모두 다 읽어서 한줄 씩 리스트 항목에 대입됨
  f.close()
  
  print(lines)
  
   - ['2 * 1 = 2\n', '2 * 2 = 4\n', '2 * 3 = 6\n', '2 * 4 = 8\n', '2 * 5 = 10\n']
   			# 개행문자(\n)도 포함되어있음
  ```

  ```python
  f = open("two_times_table.txt")
  lines = f.readlines()		# 파일의 데이터를 모두 다 읽어서 lines에 저장(리스트 type)
  f.close()
  for line in lines :			# list를 <반복 범위>로 지정해서 반복문
      print(line, end="")		# 리스트 항목마다 개행문자가 있으므로 end인자를 빈 문자열로 지정
      
    - 2 * 1 = 2
  	2 * 2 = 4
  	2 * 3 = 6
  	2 * 4 = 8
  	2 * 5 = 10
  ```

  ```python
  ## 위의 코드를 조금 더 간단하게 작성
  ## f.readlines()를 변수 lines에 대입하지 않고
  ## for문의 <반복 범위>를 바로 f.readlines()로 지정
  
  f = open("two_times_table.txt")
  for line in f.readlines() : 		# 또는 f.readlines() 대신 f만 입력해도 됨
  	print(line, end = "")
  	
    - 2 * 1 = 2
  	2 * 2 = 4
  	2 * 3 = 6
  	2 * 4 = 8
  	2 * 5 = 10
  ```

- `with open('file name', 'mode') as f :`

  ​		`<code block>`

  - `<code block>`의 코드가 모두 끝나면 `open()`으로 열린 파일 객체는 자동으로 닫힘

  ```python
  with open('myTextFile2.txt', 'w') as f :		# with를 사용하면 close()할 필요없음
      f.write('File read/write test2 : line1 \n')
      f.write('File read/write test2 : line2 \n')	# <code block> 부분이 끝나면 자동으로 
      f.write('File read/write test2 : line3 \n') # 파일객체가 닫힘
  
  !cat myTextFile2.txt				# write확인
   
    - File read/write test2 : line1 
  	File read/write test2 : line2 
  	File read/write test2 : line3 
  ```

  

