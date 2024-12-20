> # 2.1 입출력과 변수

> ## 2.1.1 입력
### 데이터 특성에 따른 데이터 분류
![데이터 특성에 따른 데이터 분류](/img/데이터%20특성에%20따른%20데이터%20분류.png)

### R에서의 데이터 타입
![R에서의 데이터 타입](/img/R에서의%20데이터%20타입.png)

> ### 숫자형 데이터
|종류|의미|
|---|---|
|int, integer|정수|
|num, numeric|실수, R에서 숫자 디폴트는 실수|
|cplx, complex|복소수|

- R에서 숫자 디폴트는 실수
```
> x= 5
> typeof(x)
[1] "double"
> typeof(5)
[1] "double"
```
```
> y= 5L # 정수형으로 입력하기
> typeof(y)
[1] "integer"
> typeof(5L)
[1] "integer"
```

### 숫자의 자릿수
- 기본적으로 7자리로 표현한다.
```
> pi
[1] 3.141593
> getOption("digits") #현재 표현하고 있는 숫자 수
[1] 7
> options(digits=4) # 4개 숫자 표현으로 변경
> getOption("digits")
[1] 4
> pi
[1] 3.142
```

> ### 문자형 데이터
- 따옴표 붙여서 입력
- 여러 값 입력할 때는 **C()** 함수 사용: 벡터 생성
|c(1, 2, 3)|[1] 1 2 3|
|c('a', 'b', 'c')|[1] "a" "b" "c"|
|c(1,2,'a')|[1] "1" "2" "a"|
- 벡터에 문자열이 섞여있으면 숫자도 모두 문자열로 출력

### 연속 벡터(수열 벡터) 생성
1. : 를 사용하기
```
> 1:5
[1] 1 2 3 4 5
> 1:-5
[1] 1 0 -1 -2 -3 -4 -5
```
2. seq 함수를 사용해서  1~ 10 범위에서 2씩 증가하는 수열 생성
```
> seq(1, 10, by=2)
[1] 1 3 5 7 9
```
3. seq 함수를 사용해서  1~ 10 구간에서 5개의 등차수열 생성
```
> seq(1, 10, length.out= 5)
[1]  1.00 3.25 5.50 7.75 10.00
```
- 실수형으로 나온다.

4. seq 함수를 사용해서 5에서 -5까지 데이터 생성
```
> seq(5,-5)
[1] 5 4 3 2 1 0 -1 -2 -3 -4 -5
```

### scan() 사용자입력
-  scan() 함수는 R에서 외부 파일 또는 사용자 입력을 읽어들이는 데 사용
- 주로 텍스트 파일이나 숫자 데이터를 한 번에 여러 개 읽을 때 사용. 
- scan() 함수는 벡터로 데이터를 반환
- 기본적으로 숫자 데이터를 읽지만, 텍스트나 다른 형식의 데이터도 처리 가능

- 기본적인 scan 함수 사용법
  - 숫자 입력
  ```r
  x <- scan()
  1: 10
  2: 20
  3:
  Read 2 items

  > y
  [1] 10 20
  ```
  ```r
  y <- scan(n=1) # 숫자 하나로 제한
  1: 100 200 300
  Read 1 items

  > y
  [1] 100
  ```
  - 텍스트 입력
  ```r
  z <-scan(what="")
  1: 1
  2: "나"
  3: 다
  4:

  Read 3 itmes

  > z
  [1] "1" "나" "다"
  ```

- scan 함수
```
scan(file = "", what = numeric(), sep = "", nmax = -1, ...)
```
- file: 읽고자 하는 파일의 경로를 지정합니다. 파일이 없으면 기본적으로 콘솔에서 입력을 받습니다.
- what: 읽을 데이터의 형식을 지정합니다. 기본값은 숫자(numeric()), 텍스트를 읽으려면 character()를 지정합니다.
- sep: 데이터 구분자를 지정합니다. 기본값은 공백입니다.
- nmax: 최대 읽을 값의 수를 지정합니다. 기본값은 파일 전체를 읽습니다.
- quiet: TRUE로 설정하면 읽을 때 나타나는 메시지를 표시하지 않습니다.

> ## 2.1.2 출력
### print()
```
print("Hello World!") # 문자 출력
print(100 + 200) # 사칙연산 출력
print(1); print(2) # 각 호출이 기본적으로 새로운 줄에서 결과를 출력.
```

### 여러 명령어 한줄에 작성하여 출력
```
print(1);print(2);print('a');print('b')
```
- 세미콜론은 명령어(문장)를 구분하는 역할을 한다.

### 여러 객체를 출력할 때
1. C() 함수를 사용하여 벡터화
```
print(C(1,2,3))
```
2. cat() 함수를 사용
```
cat(1,2,3)
```

> ## 2.1.3 변수
- 변수: 데이터를 할당하는데 사용되는 이름이 붙은 공간

### 할당의 여러가지 방법들
```
# 변수 x에  1을 할당
x <- 1 
x = 1
a <<- 1
1 -> x
assign("x", 1)
(x=1)
```
```
# 하나의 변수에 여러 개의 값을 할당
y <- c(1,2,3) 
assign("y", c(1,2,3))
```
```
# 하나의 값을 여러 개의 변수에 할당
a <- b <- 7
```

> #2.2 작업환경 관리
### 패키지 관련 함수
- install.packages("패키지이름"): CRAN에서 패키지를 다운로드하고 설치합니다.
- remove.packages("패키지이름"): 설치된 패키지를 제거합니다.
- update.packages(): 설치된 패키지들을 업데이트합니다.
- download.packages("패키지이름"): 패키지를 다운로드만 하고 설치는 하지 않습니다.
- available.packages(): 사용 가능한 패키지들의 목록을 가져옵니다.
- installed.packages(): 현재 설치된 패키지들의 목록을 가져옵니다.
- library(패키지이름): 패키지를 메모리에 로드합니다.
- require(패키지이름): 패키지를 로드하되, 패키지가 없으면 경고를 출력하고 실행을
중단하지 않는다
- detach("package:패키지이름"): 로드된 패키지를 메모리에서 분리합니다. <br>(detach() 함수는 문자열을 사용할 때도 있지만, 패키지와 함께 사용하는 경우는 객체처럼 처리합니다.)

### 현재 작업 위치
- getwd() #현재 작업이 이루어지고 있는 디렉토리 위치
- setwd("c:/data") # 작업 디렉토리를 변경
- getwd() # 바꾼 공간 확인
- list.files() #현재 작업공간에 있는 파일 확인
- dir() ##현재 작업공간에 있는 파일 확인
