> # 1. R&R studio 사용법 및 패키지

### R에 내장된 데이터 확인
```
library(help=datasets) #R에 저장된 기본 데이터 목록을 보여준다.
```

### R에서 iris 데이터 읽기
```
iris # 전체 데이터 출력
head(iris) #첫 6개 행의 데이터 출력
str(iris) #iris 데이터의 구조를 출력
```

### 패키지 설치
```
.libPaths() # 패키지 설치 경로 확인
install.packages(“openxlsx”) # 패키지 설치
library(openxlsx) # 패키지 로딩
write.xlsx() # 데이터를 엑셀 파일로 저장, # write.xlsx(data, 'c:/data/iris_2024.xlsx')
```

### iris_2024.xlsx로 저장한 데이터 읽어 오기
```
library(readxl) # .xlsx 파일 로딩딩
iris_2024 = read_excel('c:/data/iris_2024.xlsx’)
iris_2024 #엑셀 파일을 'iris_2024'변수로 저장
```

### 메모리 관리
```
ls() # 현재 메모리에 있는 것 확인: Environment 창
rm(list=ls())  # 현재 메모리에 있는 것 모두 지우기
```
#### 패키지 설치
```
install.packages("ggplot2")
install.packages( c(“ggplot2”, “caret”)
```
#### 패키지 삭제
```
remove.packages("ggplot2")
```

#### 패키지 로딩
```
library(ggplot2) # 패키지 로드 실패 시 에러 및 경고 메시지를 보낸다.
require(ggplot2)
# 성공적으로 설치되면 TRUE 반환하고
# 그렇지 않으면 FALSE 경고를 보낸다
* 메시지 안 뜨게 하는 법
suppressMessages(require(ggplot2))
```
| 기능                         | `library()`                         | `require()`                        |
|--------|-----------|---------|
| 패키지 로드 실패 시          | 에러 발생 (프로그램 중단)           | 경고 메시지 출력 (FALSE 반환)     |
| 반환값                      | 없음                                | TRUE 또는 FALSE                   |
| 사용 목적                   | 필수 패키지 로드 시 사용             | 조건부로 패키지 로드 시 사용      |

### 패키지 언로딩
```
detach(package:ggplot2)
```

### 패키지 작업환경 확인

| 함수  | 역할/주요 용도    |
|-------------|--------------|
| installed.packages()      | R에 설치된 모든 패키지 목록 조회<br>패키지 설치 상태와 정보를 확인          |
| search()   |  현재 메모리에 로딩된 패키지 확인   |
| packageVersion()   | 패키지 버전 확인  |
| update.packages()   | 패키지 업데이트  |


 
 