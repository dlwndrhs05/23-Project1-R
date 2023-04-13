# 이중곤

## 2023-04-13

### 파일 입출력할때 알아야 할 내용
### 1. 실행 결과를 파일로 출력
```R
    > setwd('Projects/23-Project1-R/')          #작업폴더

    > print('Begin work')                       #화면출력
        [1] "Begin work"

    > a<-10;b<-20

    > sink('result.txt',append=T)               #출력 시작,출력할 파일이름,내용 맨마지막에 추가
                                                #append=F를 사용시 기존 내용 삭제 후 작성

    > cat('a+b=',a+b,'\n')

    > sink()                                    #출력 중지

    > sink('result.txt',append=T)

    > cat('a*b=',a*b,'\n')

    > sink()

    > print('End work')
        [1] "End work"
```
### 2.탭이나 공백으로 분리된 파일 읽기

## 2023-04-06

### 행과 열에 이름 붙히기

```R
    > score <- matrix(c(90,85,69,78,85,96,49,95,90,80,70,60), nrow=4)

    > score
        [,1] [,2] [,3]
    [1,]   90   85   90
    [2,]   85   96   80
    [3,]   69   49   70
    [4,]   78   95   60

    > rownames(score) <-c('John','Tom','Mark','Jane') #행의 이름

    > colnames(score) <-c('English','Math','Science') #열의 이름

    > score
        English Math Science
    John      90   85      90
    Tom       85   96      80
    Mark      69   49      70
    Jane      78   95      60

    > score['John','Math']
    [1] 85

    > score['Tom',c('Math','Science')]
   Math Science 
     96      80 

    > score['Mark',]            #마크의 모든 성적
    English    Math Science 
        69      49      70 
    > score[,'English']         #모든학생의 영어성적
    John  Tom Mark Jane 
    90   85   69   78 

    > rownames(score)
    [1] "John" "Tom"  "Mark" "Jane"
    > colnames(score)
    [1] "English" "Math"    "Science"
    > colnames(score)[2]
    [1] "Math"
    
```
### 데이터프레임
* 데이터 프레임은 매트릭스와 마찬가지로 2차원 형태의 데이터를 저장하고 분석되는데 사용된다.  
동일한 자료형을 갖는 2차원형태의 자료는 매트릭스에 서로다른 자료형을 갖는 2차원 형태의
자료는 데이터 프레임에 저장하여 사용하면 된다.
### 1.데이터 프레임 만들기
```R
    > city <-c("Seoul","Tokyo","Washington")
    > rank <-c(1,3,2)
    > city.info <- data.frame(city,rank)
    > city.info
            city rank
    1      Seoul    1
    2      Tokyo    3
    3 Washington    2
```
### 2.iris 데이터셋
* iris 데이터셋은 데이터 프레임을 연습에 사용되는 R에서 제공되는 데이터 셋으로  
R에 기본적으로 저장이 되어 있어 바로 이용이 가능하다.
```R
    #iris 데이터셋
    > iris
        Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
    1            5.1         3.5          1.4         0.2     setosa
    2            4.9         3.0          1.4         0.2     setosa
    3            4.7         3.2          1.3         0.2     setosa
    4            4.6         3.1          1.5         0.2     setosa
    5            5.0         3.6          1.4         0.2     setosa
    6            5.4         3.9          1.7         0.4     setosa
    7            4.6         3.4          1.4         0.3     setosa
    8            5.0         3.4          1.5         0.2     setosa
    9            4.4         2.9          1.4         0.2     setosa
    10           4.9         3.1          1.5         0.1     setosa

    150          5.9         3.0          5.1         1.8  virginica

    > iris[1:5,]            # 1~5행의 모든 데이터
    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    1          5.1         3.5          1.4         0.2  setosa
    2          4.9         3.0          1.4         0.2  setosa
    3          4.7         3.2          1.3         0.2  setosa
    4          4.6         3.1          1.5         0.2  setosa
    5          5.0         3.6          1.4         0.2  setosa

    > iris[1:5,c(1,3)]      # 1~5행의 데이터 중 1,3열의 데이터
    Sepal.Length Petal.Length
    1          5.1          1.4
    2          4.9          1.4
    3          4.7          1.3
    4          4.6          1.5
    5          5.0          1.4
```
### 매트릭스와 데이터 프레임
* 매트릭스와 데이터 프레임은 모두 2차원 형태의 데이터를 저장하는 자료구조이기 때문에  
다루는 대부분의 방법이 동일하지만 명령문이나 함수에 따라서 적용되는 구조가 다르다.
### 1. 데이터셋의 기본 정보
```R
    > dim(iris)     #행과 열의 개수 보이기
    [1] 150   5

    > nrow(iris)    # 행의 개수 보이기
    [1] 150

    > ncol(iris)    # 열의 개수 보이기
    [1] 5

    > colnames(iris)    #열 이름 보이기,names()함수와 결과 동일
    [1] "Sepal.Length" "Sepal.Width"  "Petal.Length" "Petal.Width"  "Species"  

    > head(iris)    # 데이터셋의 앞부분 일부 보기
    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    1          5.1         3.5          1.4         0.2  setosa
    2          4.9         3.0          1.4         0.2  setosa
    3          4.7         3.2          1.3         0.2  setosa
    4          4.6         3.1          1.5         0.2  setosa
    5          5.0         3.6          1.4         0.2  setosa
    6          5.4         3.9          1.7         0.4  setosa

    > tail(iris)    # 데이터셋의 뒷부분 일부 보기
        Sepal.Length Sepal.Width Petal.Length Petal.Width   Species
    145          6.7         3.3          5.7         2.5 virginica
    146          6.7         3.0          5.2         2.3 virginica
    147          6.3         2.5          5.0         1.9 virginica
    148          6.5         3.0          5.2         2.0 virginica
    149          6.2         3.4          5.4         2.3 virginica
    150          5.9         3.0          5.1         1.8 virginica

    > str(iris)     # 데이터셋 요약 정보 보기
    'data.frame':	150 obs. of  5 variables:
    $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
    $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
    $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
    $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
    $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...

    > iris[,5]      #품종 데이터 보기
    [1] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
    [9] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
    [17] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
    [25] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
    [33] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
    [41] setosa     setosa     setosa     setosa     setosa     setosa     setosa     setosa    
    [49] setosa     setosa     versicolor versicolor versicolor versicolor versicolor versicolor
    [57] versicolor versicolor versicolor versicolor versicolor versicolor versicolor versicolor
    [65] versicolor versicolor versicolor versicolor versicolor versicolor versicolor versicolor
    [73] versicolor versicolor versicolor versicolor versicolor versicolor versicolor versicolor
    [81] versicolor versicolor versicolor versicolor versicolor versicolor versicolor versicolor
    [89] versicolor versicolor versicolor versicolor versicolor versicolor versicolor versicolor
    [97] versicolor versicolor versicolor versicolor virginica  virginica  virginica  virginica 
    [105] virginica  virginica  virginica  virginica  virginica  virginica  virginica  virginica 
    [113] virginica  virginica  virginica  virginica  virginica  virginica  virginica  virginica 
    [121] virginica  virginica  virginica  virginica  virginica  virginica  virginica  virginica 
    [129] virginica  virginica  virginica  virginica  virginica  virginica  virginica  virginica 
    [137] virginica  virginica  virginica  virginica  virginica  virginica  virginica  virginica 
    [145] virginica  virginica  virginica  virginica  virginica  virginica 
    Levels: setosa versicolor virginica

    > levels(iris[,5])  # 품종의 종류 보기(중복 제거)
    [1] "setosa"     "versicolor" "virginica" 

    > table(iris[,"Species"])   # 품종의 종류별 행의 개수 세기

        setosa versicolor  virginica 
            50         50         50 
```
### 2. 매트릭스와 데이터프레임에 함수 사용
```R
    # 행별,열별로 합계와 평균을 계산하는 함수

    > colSums(iris[,-5])    # 열별 합계
        Sepal.Length  Sepal.Width Petal.Length  Petal.Width 
        876.5        458.6        563.7        179.9 
    > colMeans(iris[,-5])   # 열별 평균
        Sepal.Length  Sepal.Width Petal.Length  Petal.Width 
        5.843333     3.057333     3.758000     1.199333 
    > rowSums(iris[,-5])    # 행별 합계
        [1] 10.2  9.5  9.4  9.4 10.2 11.4  9.7 10.1  8.9  9.6 10.8 10.0  9.3  8.5 11.2 12.0 11.0 10.3 11.5
        [20] 10.7 10.7 10.7  9.4 10.6 10.3  9.8 10.4 10.4 10.2  9.7  9.7 10.7 10.9 11.3  9.7  9.6 10.5 10.0
        [39]  8.9 10.2 10.1  8.4  9.1 10.7 11.2  9.5 10.7  9.4 10.7  9.9 16.3 15.6 16.4 13.1 15.4 14.3 15.9
        [58] 11.6 15.4 13.2 11.5 14.6 13.2 15.1 13.4 15.6 14.6 13.6 14.4 13.1 15.7 14.2 15.2 14.8 14.9 15.4
        [77] 15.8 16.4 14.9 12.8 12.8 12.6 13.6 15.4 14.4 15.5 16.0 14.3 14.0 13.3 13.7 15.1 13.6 11.6 13.8
        [96] 14.1 14.1 14.7 11.7 13.9 18.1 15.5 18.1 16.6 17.5 19.3 13.6 18.3 16.8 19.4 16.8 16.3 17.4 15.2
        [115] 16.1 17.2 16.8 20.4 19.5 14.7 18.1 15.3 19.2 15.7 17.8 18.2 15.6 15.8 16.9 17.6 18.2 20.1 17.0
        [134] 15.7 15.7 19.1 17.7 16.8 15.6 17.5 17.8 17.4 15.5 18.2 18.2 17.2 15.7 16.7 17.3 15.8
    > rowMeans(iris[,-5])   # 행별 평균
        [1] 2.550 2.375 2.350 2.350 2.550 2.850 2.425 2.525 2.225 2.400 2.700 2.500 2.325 2.125 2.800 3.000
        [17] 2.750 2.575 2.875 2.675 2.675 2.675 2.350 2.650 2.575 2.450 2.600 2.600 2.550 2.425 2.425 2.675
        [33] 2.725 2.825 2.425 2.400 2.625 2.500 2.225 2.550 2.525 2.100 2.275 2.675 2.800 2.375 2.675 2.350
        [49] 2.675 2.475 4.075 3.900 4.100 3.275 3.850 3.575 3.975 2.900 3.850 3.300 2.875 3.650 3.300 3.775
        [65] 3.350 3.900 3.650 3.400 3.600 3.275 3.925 3.550 3.800 3.700 3.725 3.850 3.950 4.100 3.725 3.200
        [81] 3.200 3.150 3.400 3.850 3.600 3.875 4.000 3.575 3.500 3.325 3.425 3.775 3.400 2.900 3.450 3.525
        [97] 3.525 3.675 2.925 3.475 4.525 3.875 4.525 4.150 4.375 4.825 3.400 4.575 4.200 4.850 4.200 4.075
        [113] 4.350 3.800 4.025 4.300 4.200 5.100 4.875 3.675 4.525 3.825 4.800 3.925 4.450 4.550 3.900 3.950
        [129] 4.225 4.400 4.550 5.025 4.250 3.925 3.925 4.775 4.425 4.200 3.900 4.375 4.450 4.350 3.875 4.550
        [145] 4.550 4.300 3.925 4.175 4.325 3.950
```
```R
    #행과 열의 방향을 바꾸는 함수

    > z <-matrix(1:20,nrow=4,ncol=5)

    > z
        [,1] [,2] [,3] [,4] [,5]
    [1,]    1    5    9   13   17
    [2,]    2    6   10   14   18
    [3,]    3    7   11   15   19
    [4,]    4    8   12   16   20

    > t(z)  #행과 열의 방향 전환
        [,1] [,2] [,3] [,4]
    [1,]    1    2    3    4
    [2,]    5    6    7    8
    [3,]    9   10   11   12
    [4,]   13   14   15   16
    [5,]   17   18   19   20
```
```R
        #특정한 조건에 맞는 값들을 추출하는 subset()함수
    IR.1 <- subset(iris, Species=='setosa')
    > IR.1
        Sepal.Length Sepal.Width Petal.Length Petal.Width Species
        1           5.1         3.5          1.4         0.2  setosa
        2           4.9         3.0          1.4         0.2  setosa
        3           4.7         3.2          1.3         0.2  setosa
        4           4.6         3.1          1.5         0.2  setosa
        5           5.0         3.6          1.4         0.2  setosa
        6           5.4         3.9          1.7         0.4  setosa
        7           4.6         3.4          1.4         0.3  setosa
        8           5.0         3.4          1.5         0.2  setosa
        9           4.4         2.9          1.4         0.2  setosa
        10          4.9         3.1          1.5         0.1  setosa
        11          5.4         3.7          1.5         0.2  setosa
        12          4.8         3.4          1.6         0.2  setosa
        13          4.8         3.0          1.4         0.1  setosa
        14          4.3         3.0          1.1         0.1  setosa
        15          5.8         4.0          1.2         0.2  setosa
        16          5.7         4.4          1.5         0.4  setosa
        17          5.4         3.9          1.3         0.4  setosa
        18          5.1         3.5          1.4         0.3  setosa
        19          5.7         3.8          1.7         0.3  setosa
        20          5.1         3.8          1.5         0.3  setosa
        21          5.4         3.4          1.7         0.2  setosa
        22          5.1         3.7          1.5         0.4  setosa
        23          4.6         3.6          1.0         0.2  setosa
        24          5.1         3.3          1.7         0.5  setosa
        25          4.8         3.4          1.9         0.2  setosa
        26          5.0         3.0          1.6         0.2  setosa
        27          5.0         3.4          1.6         0.4  setosa
        28          5.2         3.5          1.5         0.2  setosa
        29          5.2         3.4          1.4         0.2  setosa
        30          4.7         3.2          1.6         0.2  setosa
        31          4.8         3.1          1.6         0.2  setosa
        32          5.4         3.4          1.5         0.4  setosa
        33          5.2         4.1          1.5         0.1  setosa
        34          5.5         4.2          1.4         0.2  setosa
        35          4.9         3.1          1.5         0.2  setosa
        36          5.0         3.2          1.2         0.2  setosa
        37          5.5         3.5          1.3         0.2  setosa
        38          4.9         3.6          1.4         0.1  setosa
        39          4.4         3.0          1.3         0.2  setosa
        40          5.1         3.4          1.5         0.2  setosa
        41          5.0         3.5          1.3         0.3  setosa
        42          4.5         2.3          1.3         0.3  setosa
        43          4.4         3.2          1.3         0.2  setosa
        44          5.0         3.5          1.6         0.6  setosa
        45          5.1         3.8          1.9         0.4  setosa
        46          4.8         3.0          1.4         0.3  setosa
        47          5.1         3.8          1.6         0.2  setosa
        48          4.6         3.2          1.4         0.2  setosa
        49          5.3         3.7          1.5         0.2  setosa
        50          5.0         3.3          1.4         0.2  setosa

    > IR.2 <-subset(iris, Sepal.Length>5.0 & Sepal.Width>4.0)

    > IR.2
        Sepal.Length Sepal.Width Petal.Length Petal.Width Species
        16          5.7         4.4          1.5         0.4  setosa
        33          5.2         4.1          1.5         0.1  setosa
        34          5.5         4.2          1.4         0.2  setosa

    > IR.2[,c(2,4)] 
        Sepal.Width Petal.Width
        16         4.4         0.4
        33         4.1         0.1
        34         4.2         0.2
```
```R
    #산술연산
    > a<-matrix(1:20,4,5)

    > b<-matrix(21:40,4,5)

    > a
        [,1] [,2] [,3] [,4] [,5]
    [1,]    1    5    9   13   17
    [2,]    2    6   10   14   18
    [3,]    3    7   11   15   19
    [4,]    4    8   12   16   20

    > b
        [,1] [,2] [,3] [,4] [,5]
    [1,]   21   25   29   33   37
    [2,]   22   26   30   34   38
    [3,]   23   27   31   35   39
    [4,]   24   28   32   36   40

    > 2*a
        [,1] [,2] [,3] [,4] [,5]
    [1,]    2   10   18   26   34
    [2,]    4   12   20   28   36
    [3,]    6   14   22   30   38
    [4,]    8   16   24   32   40

    > a+b
        [,1] [,2] [,3] [,4] [,5]
    [1,]   22   30   38   46   54
    [2,]   24   32   40   48   56
    [3,]   26   34   42   50   58
    [4,]   28   36   44   52   60

    #값 변경

    > a<-a*3 

    > b<-b-5
```
### 3. 매트릭스와 데이터프레임의 자료구조 확인과 변환
*   매트릭스와 데이터프레임은 2차원 형태의 자료구조 이기 때문에 확인 할 수단이 필요하며  
필요시에는 매트릭스를 데이터프레임으로, 데이터프레임을 매트릭스로 변환을 할 수 있어야 한다.
```R
    > class(iris)           # 데이터셋의 자료구조 확인
        [1] "data.frame"

    > class(state.x77)      
        [1] "matrix" "array" 

    > is.matrix(iris)       # 데이터셋이 매트릭스인지 확인
        [1] FALSE

    > is.data.frame(iris)   # 데이터셋이 데이터프레임인지 확인
        [1] TRUE

    > is.matrix(state.x77)
        [1] TRUE

        # 매트릭스를 데이터 프레임으로 변환
    > is.matrix(state.x77)
        [1] TRUE
    
    > is.matrix(state.x77)
        [1] TRUE

    > st<-data.frame(state.x77)

    > head(st)
                Population Income Illiteracy Life.Exp Murder HS.Grad Frost  Area
    Alabama          3615   3624        2.1    69.05   15.1    41.3    20  50708
    Alaska            365   6315        1.5    69.31   11.3    66.7   152 566432
    Arizona          2212   4530        1.8    70.55    7.8    58.1    15 113417
    Arkansas         2110   3378        1.9    70.66   10.1    39.9    65  51945
    California      21198   5114        1.1    71.71   10.3    62.6    20 156361
    Colorado         2541   4884        0.7    72.06    6.8    63.9   166 103766
    
    > class(st)
        [1] "data.frame"

        #데이터 프레임을 매트릭스로 변환
    > is.data.frame(iris[.1:4])
        [1] TRUE

    > is.data.frame(iris[,1:4])
        [1] TRUE

    > iris.m <- as.matrix(iris[,1:4])

    > head(iris.m)
            Sepal.Length Sepal.Width Petal.Length Petal.Width
        [1,]          5.1         3.5          1.4         0.2
        [2,]          4.9         3.0          1.4         0.2
        [3,]          4.7         3.2          1.3         0.2
        [4,]          4.6         3.1          1.5         0.2
        [5,]          5.0         3.6          1.4         0.2
        [6,]          5.4         3.9          1.7         0.4

    > class(iris.m)
        [1] "matrix" "array"
```
### 4. 데이터프레임만 적용되는 열 추출 방법

### 데이터의 입력과 출력

### 1.R에서의 입력과 출력

### 2.화면에서 데이터 입력받기

### 3.print() 함수와 cat() 함수

### 파일을 이용해 데이터를 읽고 쓰기

### 1.작업 폴더 확인

### 2. csv확장자 파일 읽기와 쓰기

### 3. 엑셀 파일 읽기와 쓰기

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
