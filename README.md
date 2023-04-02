# 이중곤

## 2023-03-39

### 자료의 종류
### 1. 자료분석의 목적
 * 자료에 담겨있는 어떤 종류의 정보나 지식을 추출하고  
    이를 통해 현실을 이해하거나 현실의 문제를 해결하는 데 활용
    

### 2. 1차원 자료와 2차원자료
 * 1차원 자료는 단일 주제에 대한 값을 모아 놓은 것
 * 2차원 자료는 복수 주제에 대한 값들을 모아 놓은 것


### 3. 범주형 자료와 수치형 자료
 * 범주형 자료란 분류의 의미를 가지고 있는 값들로 구선됭 자료를 뜻 함
 * 수치형 자료는 값들이 크기를 가지며 산술연산이 가능한 값들로 구성된 자료를 뜻 함


 ### 벡터 연산
### 1. 벡터에 대한 산술연산
* 벡터에 대한 산술연산에서 주의 할 점은  
  2*d를 실행하여도 실제 벡터의 값은 변하지 않고 단순 출력만 할 뿐이며  
  벡터의 값을 변경하고 싶으면 d <-2* 를 사용하면 벡터의 값읇 변경할 수 있다
 ```R
    > d <-c(1,4,3,7,8)

    > 2*d
      [1] 2 8 6 14 16

    > d-5
      [1] -4 -1 -2 2 3

    > 3*d + 4
      [1] 7 16 13 25 28
 ```
2. 벡터와 벡터의 연산
 * 백터와 벡터간의 산술연산은 벡터 간 대응되는 위치에 있는 값들끼리의  
   연산으로 바뀌어 실행된다.
```R
    > x <-c(1,4,3,7,8)

    > y <-c(5,6,7,8)

    > x+y
    [1] 6 8 10 12

    > x * y
    [1] 5 12 21 32

    > z <-c(5,6,7,8)

    > z
    [1] 6 8 10 12

    > m <-c(x,y)

    > m
    [1] 1 2 3 4 5 6 7 8


    > n <-c(y,x)

    > n
    [1] 5 6 7 8 1 2 3 4

    > p <-c(x,y,90,100)

    > p
    [1] 1 2 3 4 5 6 7 8 90 100

 ```
  * 숫자 벡터와 문자 벡터를 결합하면 숫자값이 문자로 변환되어 결합된다.
```R
    > v1 <- c(1,2,3,4)
    
    > v2 <- c('John','Jane','Tom')
    
    > v3 <- c(v1,v2)
    
    > v3
    [1] "1" "2" "3" "4" "John" "Jane" "Tom"
```
3. 벡터에 적용 가능한 함수
 * 벡터에서도 산술연산에 쓰이는 함수들을 사용할 수가 있다
```R
    > d < - c(1,2,3,4,5,6,7,8,9,10)

     > sum(d)
    [1] 55

    > sum(2*d)
    [1] 110

    > length(d)
    [1] 10

    > mean(d[1:5])
    [1] 3

    > max(d)
    [1] 10

    > min(d)
    [1] 1

    > sort(d)
    [1] 1 2 3 4 5 6 7 8 9 10

    > sort(d, decreasing = FALSE)
    [1] 1 2 3 4 5 6 7 8 9 10

    > sort(d, decreasing = TRUE)
    [1] 10 9 8 7 6 5 4 3 2 1
```
4. 벡터에 논리 연산자 적용
 * 논리 연산자도 산술연산자와 같이 각각의 값에 대한 연산으로 실행되게 된다.
 ```R
    > d <- 1:9
    
    > d>=5
    [1]FALSE FALSE FALSE FALSE TRUE TRUE TRUE TRUE TRUE

    > d[d>5]
    [1] 6 7 8 9

    >sum(d>5)
    [1] 4

    > sum(d[d>5]) #5보다 큰값의 총합
    [1] 30

    > condi <- d > 5 & d < 8 #변수에 조건값을 저장할 수 있다

    > d[condi]
    [1] 6 7
 ```

### 팩터와 리스트
1. 팩터
 * 문자형 데이터 베이스가 저장되는 벡터의 일종  
   저장되는 문자값들이 어떠한 종류를 나타내는 값일 때 사용
   펙터는 문자형 벡터를 만든 다음 factor() 함수를 이용하여 변환하여 만들수 있다.
```R
    > bt <- c('A','B','B','O','AB','A')

    > bt.new <- factor(bt)
    
    > bt
    [1] "A"  "B"  "B"  "O"  "AB" "A" 
    
    > bt.new
    [1] A  B  B  O  AB A 
    Levels: A AB B O        #팩터의 목적이 어떤 종류를 나타내는 문자값의 저장이기 때문에 정보를 자동으로 보여줌
    
    > bt[5]
    [1] "AB"
    
    > bt.new[5]
    [1] AB
    Levels: A AB B O

    > bt.new[7] <- 'B'

    > bt.new[8] <- 'C'
    Warning message:
    In `[<-.factor`(`*tmp*`, 8, value = "C") :
    invalid factor level, NA generated

    > bt.new
    [1] A    B    B    O    AB   A    B    <NA>
    Levels: A AB B O
```
2. 리스트
 * 자료형이 다른 값들을 한곳에 저장하고 다룰 수 있도록 해주는 수단
 ```R
 > h.list <- c('balling','temmis','ski')
    > person <- list(name = 'tom', age=25 ,student=TRUE,hobby=h.list)
    > person
    $name
    [1] "tom"

    $age
    [1] 25

    $student
    [1] TRUE

    $hobby
    [1] "balling" "temmis"  "ski"    

    > person[[1]]
    [1] "tom"

    > person$name
    [1] "tom"

    > person[[4]]
    [1] "balling" "temmis"  "ski" 
 ```

### 매트릭스
1. 2차원 자료의 저장
 * 매트릭스와 데이터 프레임은 2차원 자료를 저장하기 위한 대표적인 자료구조로  
    여러 주제로 데이터를 수집한 형태를 말하며  
    매트릭스는 같은 데이터 타입의 자료를  
    데이터 프레임은 다른 종류의 타입의 자료를 저장 할 수 있다.
 * 2차원 데이터는 테이블의 형태로 표현 되며 가로줄은 행 또는 관측값
   세로줄은 컬럼,변수라고 부른다.
2. 매트릭스 만들기
 * 매트릭스는 같은 데이터 타입의 자료를 저장하며 보통 숫자로만 구성된 2차원 자료를 저장하는데 사용된다.
```R
    > z <- matrix(1:20, nrow=4, ncol=5)
    
    > z
        [,1] [,2] [,3] [,4] [,5]
    [1,]    1    5    9   13   17
    [2,]    2    6   10   14   18
    [3,]    3    7   11   15   19
    [4,]    4    8   12   16   20
    
    > View(z) #환경창에 새로운 창과 함께 테이블이 표시된다.

    > x <-1:4

    > y <-5:8

    > z <-matrix(1:20, nrow=4,ncol=5)

    > m1 <- cbind(x,y)

    > m1
        x y
    [1,] 1 5
    [2,] 2 6
    [3,] 3 7
    [4,] 4 8

    > m2 <- rbind(x,y)

    > m2
    [,1] [,2] [,3] [,4]
    x    1    2    3    4
    y    5    6    7    8
    > m3 <- rbind(m2,x)


    > m3
    [,1] [,2] [,3] [,4]
    x    1    2    3    4
    y    5    6    7    8
    x    1    2    3    4

    > m4 <- cbind(z,x)

    > m4
                    x
    [1,] 1 5  9 13 17 1
    [2,] 2 6 10 14 18 2
    [3,] 3 7 11 15 19 3
    [4,] 4 8 12 16 20 4
```
3. 매트릭스에서 값의 추출
 * 매트릭스에서 특정 위치에 있는 값을 추출하는 방법은 벡터와 유사하며  
  2개의 인덱스 값을 지정하여 값을 추출 할 수 있다

## 2023-03-16
### R 언어의 특징

    1.데이터 분석에 특화되어 있다.

    2.탄탄한 사용자 커뮤니티를 보유하고 있다.

    3.다양한 패키지(라이브러리)를 제공한다.

    4.미적이고 기능적인 통계 그래프를 제공한다.

    5.편리한 프로그래밍 환경

### R 설치
본인은 맥북을 사용중이므로 패키지 매니저인 Homebrew를 사용했다.
```Terminal
~brew install R
```
### R 스튜디오 설치
똑같이 Homewbrew로 설치 하였다
```Terminal
~brew install Caskroom/cask/rstudio
```
### R 스튜디오의 화면 구성
 R스튜디오의 화면은 소스 영역,콘솔 영역, 환경 영역,파일 영역 4가지로 구성된다   
* 소스 영역
    소스 영역에는 소스창이 위치하며 소스 창은 R명령어를 작성하고 실행하는 영역이다   
* 콘솔 영역
    콘솔 영역에는 콘솔창을 포함하여 총 3개의 창이 위치한다.  
    콘솔 창은 소스창에서 작성한 R명령문을 실행시켯을 때 명령문의 실행 과정 및 결과가 표시된다.  
    콘솔 영역에는 터미널도 존재한다.

* 환경 영역  
    환경 영역에는 환경창을 포함하여 4개의 창이 존재한다.   
     * 환경 창  
     R명령문이 실행되는 동안 만들어지는 각종 변수나 자료구조의 내용을 표시
        
        
     * 히스토리 창  
     R 스튜디오에서 실행한 명령문,결과,패키지 설치.오류 등 거의 모든 작업 과정에 대한 이력이 표시


     * 커넥션 창  
     R과 데이터 관리를 위한 서버를 연결하는 창 잘 사용되지 않는다.


     * 튜토리얼 창  
     1.3 버전부터 업데이트 되어 R을 따라하며 배울 수 있는 구역
* 파일 영역  
    파일 영역에는 파일창을 포함하여 5개의 창이 위치한다.  
    * 파일창:윈도우 탐색기,finder의 역할을 한다.

    * 플롯창:R 명령문으로 작성한 그래프가 표시된다  

    * 패키지창:내 컴퓨터에 설치된 R패키지들의 목록을 볼 수 있고, 필요시 패키지 다운이 가능하다  

    * 도움말창:특정 함수에 대한 도움말을 찾아볼 수 있다.   
    
    * 뷰어창:분석 결과가 숫자가 아닌 이미지 형태일 때 웹 브라우저 상에 결과를 출력하는
    경우가 있는데, 그럴 경우에 뷰어창에 표시된다.  


 
## 2023-03-09
github 연결 및 저장소 추가
