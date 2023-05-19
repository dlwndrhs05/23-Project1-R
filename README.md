# 이중곤

## 2023-05-18

### 정렬
 * 정렬은 주어진 기준에 따라 데이터를 크기순으로 재배열하는 과정으로, 데이터 분석 과정에서  
 빈번하게 이루어 지며 숫자의 크기, 문자열의 알파벳,가나다 순으로 정렬을 한다.
### 1.벡터의 정렬
```R
    #숫자 정렬
    > v1 <- c(1,7,6,8,4,2,3)

    > v1 <- sort(v1)    #오름차순
    
    > v1
    [1] 1 2 3 4 6 7 8
    
    > v2 <- sort(v1,decreasing = T)     #내림차순
    
    > v2
    [1] 8 7 6 4 3 2 1  
    # sort() 함수는 기본적으로 오름차순으로 적용되며 내리마순으로 변경할 경우 함수의 매개변수 decreasing의 값을 TRUE로 바꿔준다.

    #문자열 정렬
    > name <-c('정대일','강재구','신현석','홍길동')

    > sort(name)
    [1] "강재구" "신현석" "정대일" "홍길동"

    > sort(name,decreasing = T)
    [1] "홍길동" "정대일" "신현석" "강재구"
```
sort()말고 order()함수를 이용해서도 정렬이 가능하다.  
sort()는 값들의 크기에 따라 값들을 정렬하고  
order()는 값의 크기에 따라 값들의 인덱스를 정렬 한다.
```R
    > name <-c('정대일','강재구','신현석','홍길동')

    > order(name)
    [1] 2 3 1 4
    
    > order(name,decreasing = T)
    [1] 4 1 3 2

    > idx <-order(name)
    
    > name[idx]
    [1] "강재구" "신현석" "정대일" "홍길동"
```
### 2. 매트릭스와 데이터프레임의 정렬
 * 매트릭스와 데이터 프레임에 저장된 데이터는 특정 열의 값들을 기준으로 행들을 재배열하는 형태로  
 정렬을 하게 된다
 ```R
> head(iris)
  Sepal.Length Sepal.Width Petal.Length Petal.Width Species
1          5.1         3.5          1.4         0.2  setosa
2          4.9         3.0          1.4         0.2  setosa
3          4.7         3.2          1.3         0.2  setosa
4          4.6         3.1          1.5         0.2  setosa
5          5.0         3.6          1.4         0.2  setosa
6          5.4         3.9          1.7         0.4  setosa

> order(iris$Sepal.Length)      #주어진 값에 순서를 정함
  [1]  14   9  39  43  42   4   7  23  48   3  30  12  13  25  31  46   2  10  35  38  58
 [22] 107   5   8  26  27  36  41  44  50  61  94   1  18  20  22  24  40  45  47  99  28
 [43]  29  33  60  49   6  11  17  21  32  85  34  37  54  81  82  90  91  65  67  70  89
 [64]  95 122  16  19  56  80  96  97 100 114  15  68  83  93 102 115 143  62  71 150  63
 [85]  79  84  86 120 139  64  72  74  92 128 135  69  98 127 149  57  73  88 101 104 124
[106] 134 137 147  52  75 112 116 129 133 138  55 105 111 117 148  59  76  66  78  87 109
[127] 125 141 145 146  77 113 144  53 121 140 142  51 103 110 126 130 108 131 106 118 119
[148] 123 136 132

> iris[order(iris$Sepal.Length),]
    Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
14           4.3         3.0          1.1         0.1     setosa
9            4.4         2.9          1.4         0.2     setosa
39           4.4         3.0          1.3         0.2     setosa
43           4.4         3.2          1.3         0.2     setosa
42           4.5         2.3          1.3         0.3     setosa
4            4.6         3.1          1.5         0.2     setosa
7            4.6         3.4          1.4         0.3     setosa
23           4.6         3.6          1.0         0.2     setosa
48           4.6         3.2          1.4         0.2     setosa
3            4.7         3.2          1.3         0.2     setosa
30           4.7         3.2          1.6         0.2     setosa
12           4.8         3.4          1.6         0.2     setosa
13           4.8         3.0          1.4         0.1     setosa
25           4.8         3.4          1.9         0.2     setosa
31           4.8         3.1          1.6         0.2     setosa
46           4.8         3.0          1.4         0.3     setosa
2            4.9         3.0          1.4         0.2     setosa
10           4.9         3.1          1.5         0.1     setosa
35           4.9         3.1          1.5         0.2     setosa
38           4.9         3.6          1.4         0.1     setosa
58           4.9         2.4          3.3         1.0 versicolor
107          4.9         2.5          4.5         1.7  virginica
5            5.0         3.6          1.4         0.2     setosa
8            5.0         3.4          1.5         0.2     setosa
26           5.0         3.0          1.6         0.2     setosa
27           5.0         3.4          1.6         0.4     setosa
36           5.0         3.2          1.2         0.2     setosa
41           5.0         3.5          1.3         0.3     setosa
44           5.0         3.5          1.6         0.6     setosa
50           5.0         3.3          1.4         0.2     setosa
61           5.0         2.0          3.5         1.0 versicolor
94           5.0         2.3          3.3         1.0 versicolor
1            5.1         3.5          1.4         0.2     setosa
18           5.1         3.5          1.4         0.3     setosa
20           5.1         3.8          1.5         0.3     setosa
22           5.1         3.7          1.5         0.4     setosa
24           5.1         3.3          1.7         0.5     setosa
40           5.1         3.4          1.5         0.2     setosa
45           5.1         3.8          1.9         0.4     setosa
47           5.1         3.8          1.6         0.2     setosa
99           5.1         2.5          3.0         1.1 versicolor
28           5.2         3.5          1.5         0.2     setosa
29           5.2         3.4          1.4         0.2     setosa
33           5.2         4.1          1.5         0.1     setosa
60           5.2         2.7          3.9         1.4 versicolor
49           5.3         3.7          1.5         0.2     setosa
6            5.4         3.9          1.7         0.4     setosa
11           5.4         3.7          1.5         0.2     setosa
17           5.4         3.9          1.3         0.4     setosa
21           5.4         3.4          1.7         0.2     setosa
32           5.4         3.4          1.5         0.4     setosa
85           5.4         3.0          4.5         1.5 versicolor
34           5.5         4.2          1.4         0.2     setosa
37           5.5         3.5          1.3         0.2     setosa
54           5.5         2.3          4.0         1.3 versicolor
81           5.5         2.4          3.8         1.1 versicolor
82           5.5         2.4          3.7         1.0 versicolor
90           5.5         2.5          4.0         1.3 versicolor
91           5.5         2.6          4.4         1.2 versicolor
65           5.6         2.9          3.6         1.3 versicolor
67           5.6         3.0          4.5         1.5 versicolor
70           5.6         2.5          3.9         1.1 versicolor
89           5.6         3.0          4.1         1.3 versicolor
95           5.6         2.7          4.2         1.3 versicolor
122          5.6         2.8          4.9         2.0  virginica
16           5.7         4.4          1.5         0.4     setosa
19           5.7         3.8          1.7         0.3     setosa
56           5.7         2.8          4.5         1.3 versicolor
80           5.7         2.6          3.5         1.0 versicolor
96           5.7         3.0          4.2         1.2 versicolor
97           5.7         2.9          4.2         1.3 versicolor
100          5.7         2.8          4.1         1.3 versicolor
114          5.7         2.5          5.0         2.0  virginica
15           5.8         4.0          1.2         0.2     setosa
68           5.8         2.7          4.1         1.0 versicolor
83           5.8         2.7          3.9         1.2 versicolor
93           5.8         2.6          4.0         1.2 versicolor
102          5.8         2.7          5.1         1.9  virginica
115          5.8         2.8          5.1         2.4  virginica
143          5.8         2.7          5.1         1.9  virginica
62           5.9         3.0          4.2         1.5 versicolor
71           5.9         3.2          4.8         1.8 versicolor
150          5.9         3.0          5.1         1.8  virginica
63           6.0         2.2          4.0         1.0 versicolor
79           6.0         2.9          4.5         1.5 versicolor
84           6.0         2.7          5.1         1.6 versicolor
86           6.0         3.4          4.5         1.6 versicolor
120          6.0         2.2          5.0         1.5  virginica
139          6.0         3.0          4.8         1.8  virginica
64           6.1         2.9          4.7         1.4 versicolor
72           6.1         2.8          4.0         1.3 versicolor
74           6.1         2.8          4.7         1.2 versicolor
92           6.1         3.0          4.6         1.4 versicolor
128          6.1         3.0          4.9         1.8  virginica
135          6.1         2.6          5.6         1.4  virginica
69           6.2         2.2          4.5         1.5 versicolor
98           6.2         2.9          4.3         1.3 versicolor
127          6.2         2.8          4.8         1.8  virginica
149          6.2         3.4          5.4         2.3  virginica
57           6.3         3.3          4.7         1.6 versicolor
73           6.3         2.5          4.9         1.5 versicolor
88           6.3         2.3          4.4         1.3 versicolor
101          6.3         3.3          6.0         2.5  virginica
104          6.3         2.9          5.6         1.8  virginica
124          6.3         2.7          4.9         1.8  virginica
134          6.3         2.8          5.1         1.5  virginica
137          6.3         3.4          5.6         2.4  virginica
147          6.3         2.5          5.0         1.9  virginica
52           6.4         3.2          4.5         1.5 versicolor
75           6.4         2.9          4.3         1.3 versicolor
112          6.4         2.7          5.3         1.9  virginica
116          6.4         3.2          5.3         2.3  virginica
129          6.4         2.8          5.6         2.1  virginica
133          6.4         2.8          5.6         2.2  virginica
138          6.4         3.1          5.5         1.8  virginica
55           6.5         2.8          4.6         1.5 versicolor
105          6.5         3.0          5.8         2.2  virginica
111          6.5         3.2          5.1         2.0  virginica
117          6.5         3.0          5.5         1.8  virginica
148          6.5         3.0          5.2         2.0  virginica
59           6.6         2.9          4.6         1.3 versicolor
76           6.6         3.0          4.4         1.4 versicolor
66           6.7         3.1          4.4         1.4 versicolor
78           6.7         3.0          5.0         1.7 versicolor
87           6.7         3.1          4.7         1.5 versicolor
109          6.7         2.5          5.8         1.8  virginica
125          6.7         3.3          5.7         2.1  virginica
141          6.7         3.1          5.6         2.4  virginica
145          6.7         3.3          5.7         2.5  virginica
146          6.7         3.0          5.2         2.3  virginica
77           6.8         2.8          4.8         1.4 versicolor
113          6.8         3.0          5.5         2.1  virginica
144          6.8         3.2          5.9         2.3  virginica
53           6.9         3.1          4.9         1.5 versicolor
121          6.9         3.2          5.7         2.3  virginica
140          6.9         3.1          5.4         2.1  virginica
142          6.9         3.1          5.1         2.3  virginica
51           7.0         3.2          4.7         1.4 versicolor
103          7.1         3.0          5.9         2.1  virginica
110          7.2         3.6          6.1         2.5  virginica
126          7.2         3.2          6.0         1.8  virginica
130          7.2         3.0          5.8         1.6  virginica
108          7.3         2.9          6.3         1.8  virginica
131          7.4         2.8          6.1         1.9  virginica
106          7.6         3.0          6.6         2.1  virginica
118          7.7         3.8          6.7         2.2  virginica
119          7.7         2.6          6.9         2.3  virginica
123          7.7         2.8          6.7         2.0  virginica
136          7.7         3.0          6.1         2.3  virginica
132          7.9         3.8          6.4         2.0  virginica

> iris[order(iris$Sepal.Length,decreasing=T),]
     Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
132          7.9         3.8          6.4         2.0  virginica
118          7.7         3.8          6.7         2.2  virginica
119          7.7         2.6          6.9         2.3  virginica
123          7.7         2.8          6.7         2.0  virginica
136          7.7         3.0          6.1         2.3  virginica
106          7.6         3.0          6.6         2.1  virginica
131          7.4         2.8          6.1         1.9  virginica
108          7.3         2.9          6.3         1.8  virginica
110          7.2         3.6          6.1         2.5  virginica
126          7.2         3.2          6.0         1.8  virginica
130          7.2         3.0          5.8         1.6  virginica
103          7.1         3.0          5.9         2.1  virginica
51           7.0         3.2          4.7         1.4 versicolor
53           6.9         3.1          4.9         1.5 versicolor
121          6.9         3.2          5.7         2.3  virginica
140          6.9         3.1          5.4         2.1  virginica
142          6.9         3.1          5.1         2.3  virginica
77           6.8         2.8          4.8         1.4 versicolor
113          6.8         3.0          5.5         2.1  virginica
144          6.8         3.2          5.9         2.3  virginica
66           6.7         3.1          4.4         1.4 versicolor
78           6.7         3.0          5.0         1.7 versicolor
87           6.7         3.1          4.7         1.5 versicolor
109          6.7         2.5          5.8         1.8  virginica
125          6.7         3.3          5.7         2.1  virginica
141          6.7         3.1          5.6         2.4  virginica
145          6.7         3.3          5.7         2.5  virginica
146          6.7         3.0          5.2         2.3  virginica
59           6.6         2.9          4.6         1.3 versicolor
76           6.6         3.0          4.4         1.4 versicolor
55           6.5         2.8          4.6         1.5 versicolor
105          6.5         3.0          5.8         2.2  virginica
111          6.5         3.2          5.1         2.0  virginica
117          6.5         3.0          5.5         1.8  virginica
148          6.5         3.0          5.2         2.0  virginica
52           6.4         3.2          4.5         1.5 versicolor
75           6.4         2.9          4.3         1.3 versicolor
112          6.4         2.7          5.3         1.9  virginica
116          6.4         3.2          5.3         2.3  virginica
129          6.4         2.8          5.6         2.1  virginica
133          6.4         2.8          5.6         2.2  virginica
138          6.4         3.1          5.5         1.8  virginica
57           6.3         3.3          4.7         1.6 versicolor
73           6.3         2.5          4.9         1.5 versicolor
88           6.3         2.3          4.4         1.3 versicolor
101          6.3         3.3          6.0         2.5  virginica
104          6.3         2.9          5.6         1.8  virginica
124          6.3         2.7          4.9         1.8  virginica
134          6.3         2.8          5.1         1.5  virginica
137          6.3         3.4          5.6         2.4  virginica
147          6.3         2.5          5.0         1.9  virginica
69           6.2         2.2          4.5         1.5 versicolor
98           6.2         2.9          4.3         1.3 versicolor
127          6.2         2.8          4.8         1.8  virginica
149          6.2         3.4          5.4         2.3  virginica
64           6.1         2.9          4.7         1.4 versicolor
72           6.1         2.8          4.0         1.3 versicolor
74           6.1         2.8          4.7         1.2 versicolor
92           6.1         3.0          4.6         1.4 versicolor
128          6.1         3.0          4.9         1.8  virginica
135          6.1         2.6          5.6         1.4  virginica
63           6.0         2.2          4.0         1.0 versicolor
79           6.0         2.9          4.5         1.5 versicolor
84           6.0         2.7          5.1         1.6 versicolor
86           6.0         3.4          4.5         1.6 versicolor
120          6.0         2.2          5.0         1.5  virginica
139          6.0         3.0          4.8         1.8  virginica
62           5.9         3.0          4.2         1.5 versicolor
71           5.9         3.2          4.8         1.8 versicolor
150          5.9         3.0          5.1         1.8  virginica
15           5.8         4.0          1.2         0.2     setosa
68           5.8         2.7          4.1         1.0 versicolor
83           5.8         2.7          3.9         1.2 versicolor
93           5.8         2.6          4.0         1.2 versicolor
102          5.8         2.7          5.1         1.9  virginica
115          5.8         2.8          5.1         2.4  virginica
143          5.8         2.7          5.1         1.9  virginica
16           5.7         4.4          1.5         0.4     setosa
19           5.7         3.8          1.7         0.3     setosa
56           5.7         2.8          4.5         1.3 versicolor
80           5.7         2.6          3.5         1.0 versicolor
96           5.7         3.0          4.2         1.2 versicolor
97           5.7         2.9          4.2         1.3 versicolor
100          5.7         2.8          4.1         1.3 versicolor
114          5.7         2.5          5.0         2.0  virginica
65           5.6         2.9          3.6         1.3 versicolor
67           5.6         3.0          4.5         1.5 versicolor
70           5.6         2.5          3.9         1.1 versicolor
89           5.6         3.0          4.1         1.3 versicolor
95           5.6         2.7          4.2         1.3 versicolor
122          5.6         2.8          4.9         2.0  virginica
34           5.5         4.2          1.4         0.2     setosa
37           5.5         3.5          1.3         0.2     setosa
54           5.5         2.3          4.0         1.3 versicolor
81           5.5         2.4          3.8         1.1 versicolor
82           5.5         2.4          3.7         1.0 versicolor
90           5.5         2.5          4.0         1.3 versicolor
91           5.5         2.6          4.4         1.2 versicolor
6            5.4         3.9          1.7         0.4     setosa
11           5.4         3.7          1.5         0.2     setosa
17           5.4         3.9          1.3         0.4     setosa
21           5.4         3.4          1.7         0.2     setosa
32           5.4         3.4          1.5         0.4     setosa
85           5.4         3.0          4.5         1.5 versicolor
49           5.3         3.7          1.5         0.2     setosa
28           5.2         3.5          1.5         0.2     setosa
29           5.2         3.4          1.4         0.2     setosa
33           5.2         4.1          1.5         0.1     setosa
60           5.2         2.7          3.9         1.4 versicolor
1            5.1         3.5          1.4         0.2     setosa
18           5.1         3.5          1.4         0.3     setosa
20           5.1         3.8          1.5         0.3     setosa
22           5.1         3.7          1.5         0.4     setosa
24           5.1         3.3          1.7         0.5     setosa
40           5.1         3.4          1.5         0.2     setosa
45           5.1         3.8          1.9         0.4     setosa
47           5.1         3.8          1.6         0.2     setosa
99           5.1         2.5          3.0         1.1 versicolor
5            5.0         3.6          1.4         0.2     setosa
8            5.0         3.4          1.5         0.2     setosa
26           5.0         3.0          1.6         0.2     setosa
27           5.0         3.4          1.6         0.4     setosa
36           5.0         3.2          1.2         0.2     setosa
41           5.0         3.5          1.3         0.3     setosa
44           5.0         3.5          1.6         0.6     setosa
50           5.0         3.3          1.4         0.2     setosa
61           5.0         2.0          3.5         1.0 versicolor
94           5.0         2.3          3.3         1.0 versicolor
2            4.9         3.0          1.4         0.2     setosa
10           4.9         3.1          1.5         0.1     setosa
35           4.9         3.1          1.5         0.2     setosa
38           4.9         3.6          1.4         0.1     setosa
58           4.9         2.4          3.3         1.0 versicolor
107          4.9         2.5          4.5         1.7  virginica
12           4.8         3.4          1.6         0.2     setosa
13           4.8         3.0          1.4         0.1     setosa
25           4.8         3.4          1.9         0.2     setosa
31           4.8         3.1          1.6         0.2     setosa
46           4.8         3.0          1.4         0.3     setosa
3            4.7         3.2          1.3         0.2     setosa
30           4.7         3.2          1.6         0.2     setosa
4            4.6         3.1          1.5         0.2     setosa
7            4.6         3.4          1.4         0.3     setosa
23           4.6         3.6          1.0         0.2     setosa
48           4.6         3.2          1.4         0.2     setosa
42           4.5         2.3          1.3         0.3     setosa
9            4.4         2.9          1.4         0.2     setosa
39           4.4         3.0          1.3         0.2     setosa
43           4.4         3.2          1.3         0.2     setosa
14           4.3         3.0          1.1         0.1     setosa
> iris.new <- iris[order(iris$Sepal.Length),]

> head(iris.new)
    Sepal.Length Sepal.Width Petal.Length Petal.Width Species
14          4.3         3.0          1.1         0.1  setosa
9           4.4         2.9          1.4         0.2  setosa
39          4.4         3.0          1.3         0.2  setosa
43          4.4         3.2          1.3         0.2  setosa
42          4.5         2.3          1.3         0.3  setosa
4           4.6         3.1          1.5         0.2  setosa
> iris[order(iris$Species,decreasing = T,iris$Petal.Length),]
    Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
119          7.7         2.6          6.9         2.3  virginica
118          7.7         3.8          6.7         2.2  virginica
123          7.7         2.8          6.7         2.0  virginica
106          7.6         3.0          6.6         2.1  virginica
132          7.9         3.8          6.4         2.0  virginica
108          7.3         2.9          6.3         1.8  virginica
110          7.2         3.6          6.1         2.5  virginica
131          7.4         2.8          6.1         1.9  virginica
136          7.7         3.0          6.1         2.3  virginica
101          6.3         3.3          6.0         2.5  virginica
126          7.2         3.2          6.0         1.8  virginica
103          7.1         3.0          5.9         2.1  virginica
144          6.8         3.2          5.9         2.3  virginica
105          6.5         3.0          5.8         2.2  virginica
109          6.7         2.5          5.8         1.8  virginica
130          7.2         3.0          5.8         1.6  virginica
121          6.9         3.2          5.7         2.3  virginica
125          6.7         3.3          5.7         2.1  virginica
145          6.7         3.3          5.7         2.5  virginica
104          6.3         2.9          5.6         1.8  virginica
129          6.4         2.8          5.6         2.1  virginica
133          6.4         2.8          5.6         2.2  virginica
135          6.1         2.6          5.6         1.4  virginica
137          6.3         3.4          5.6         2.4  virginica
141          6.7         3.1          5.6         2.4  virginica
113          6.8         3.0          5.5         2.1  virginica
117          6.5         3.0          5.5         1.8  virginica
138          6.4         3.1          5.5         1.8  virginica
140          6.9         3.1          5.4         2.1  virginica
149          6.2         3.4          5.4         2.3  virginica
112          6.4         2.7          5.3         1.9  virginica
116          6.4         3.2          5.3         2.3  virginica
146          6.7         3.0          5.2         2.3  virginica
148          6.5         3.0          5.2         2.0  virginica
102          5.8         2.7          5.1         1.9  virginica
111          6.5         3.2          5.1         2.0  virginica
115          5.8         2.8          5.1         2.4  virginica
134          6.3         2.8          5.1         1.5  virginica
142          6.9         3.1          5.1         2.3  virginica
143          5.8         2.7          5.1         1.9  virginica
150          5.9         3.0          5.1         1.8  virginica
114          5.7         2.5          5.0         2.0  virginica
120          6.0         2.2          5.0         1.5  virginica
147          6.3         2.5          5.0         1.9  virginica
122          5.6         2.8          4.9         2.0  virginica
124          6.3         2.7          4.9         1.8  virginica
128          6.1         3.0          4.9         1.8  virginica
127          6.2         2.8          4.8         1.8  virginica
139          6.0         3.0          4.8         1.8  virginica
107          4.9         2.5          4.5         1.7  virginica
84           6.0         2.7          5.1         1.6 versicolor
78           6.7         3.0          5.0         1.7 versicolor
53           6.9         3.1          4.9         1.5 versicolor
73           6.3         2.5          4.9         1.5 versicolor
71           5.9         3.2          4.8         1.8 versicolor
77           6.8         2.8          4.8         1.4 versicolor
51           7.0         3.2          4.7         1.4 versicolor
57           6.3         3.3          4.7         1.6 versicolor
64           6.1         2.9          4.7         1.4 versicolor
74           6.1         2.8          4.7         1.2 versicolor
87           6.7         3.1          4.7         1.5 versicolor
55           6.5         2.8          4.6         1.5 versicolor
59           6.6         2.9          4.6         1.3 versicolor
92           6.1         3.0          4.6         1.4 versicolor
52           6.4         3.2          4.5         1.5 versicolor
56           5.7         2.8          4.5         1.3 versicolor
67           5.6         3.0          4.5         1.5 versicolor
69           6.2         2.2          4.5         1.5 versicolor
79           6.0         2.9          4.5         1.5 versicolor
85           5.4         3.0          4.5         1.5 versicolor
86           6.0         3.4          4.5         1.6 versicolor
66           6.7         3.1          4.4         1.4 versicolor
76           6.6         3.0          4.4         1.4 versicolor
88           6.3         2.3          4.4         1.3 versicolor
91           5.5         2.6          4.4         1.2 versicolor
75           6.4         2.9          4.3         1.3 versicolor
98           6.2         2.9          4.3         1.3 versicolor
62           5.9         3.0          4.2         1.5 versicolor
95           5.6         2.7          4.2         1.3 versicolor
96           5.7         3.0          4.2         1.2 versicolor
97           5.7         2.9          4.2         1.3 versicolor
68           5.8         2.7          4.1         1.0 versicolor
89           5.6         3.0          4.1         1.3 versicolor
100          5.7         2.8          4.1         1.3 versicolor
54           5.5         2.3          4.0         1.3 versicolor
63           6.0         2.2          4.0         1.0 versicolor
72           6.1         2.8          4.0         1.3 versicolor
90           5.5         2.5          4.0         1.3 versicolor
93           5.8         2.6          4.0         1.2 versicolor
60           5.2         2.7          3.9         1.4 versicolor
70           5.6         2.5          3.9         1.1 versicolor
83           5.8         2.7          3.9         1.2 versicolor
81           5.5         2.4          3.8         1.1 versicolor
82           5.5         2.4          3.7         1.0 versicolor
65           5.6         2.9          3.6         1.3 versicolor
61           5.0         2.0          3.5         1.0 versicolor
80           5.7         2.6          3.5         1.0 versicolor
58           4.9         2.4          3.3         1.0 versicolor
94           5.0         2.3          3.3         1.0 versicolor
99           5.1         2.5          3.0         1.1 versicolor
25           4.8         3.4          1.9         0.2     setosa
45           5.1         3.8          1.9         0.4     setosa
6            5.4         3.9          1.7         0.4     setosa
19           5.7         3.8          1.7         0.3     setosa
21           5.4         3.4          1.7         0.2     setosa
24           5.1         3.3          1.7         0.5     setosa
12           4.8         3.4          1.6         0.2     setosa
26           5.0         3.0          1.6         0.2     setosa
27           5.0         3.4          1.6         0.4     setosa
30           4.7         3.2          1.6         0.2     setosa
31           4.8         3.1          1.6         0.2     setosa
44           5.0         3.5          1.6         0.6     setosa
47           5.1         3.8          1.6         0.2     setosa
4            4.6         3.1          1.5         0.2     setosa
8            5.0         3.4          1.5         0.2     setosa
10           4.9         3.1          1.5         0.1     setosa
11           5.4         3.7          1.5         0.2     setosa
16           5.7         4.4          1.5         0.4     setosa
20           5.1         3.8          1.5         0.3     setosa
22           5.1         3.7          1.5         0.4     setosa
28           5.2         3.5          1.5         0.2     setosa
32           5.4         3.4          1.5         0.4     setosa
33           5.2         4.1          1.5         0.1     setosa
35           4.9         3.1          1.5         0.2     setosa
40           5.1         3.4          1.5         0.2     setosa
49           5.3         3.7          1.5         0.2     setosa
1            5.1         3.5          1.4         0.2     setosa
2            4.9         3.0          1.4         0.2     setosa
5            5.0         3.6          1.4         0.2     setosa
7            4.6         3.4          1.4         0.3     setosa
9            4.4         2.9          1.4         0.2     setosa
13           4.8         3.0          1.4         0.1     setosa
18           5.1         3.5          1.4         0.3     setosa
29           5.2         3.4          1.4         0.2     setosa
34           5.5         4.2          1.4         0.2     setosa
38           4.9         3.6          1.4         0.1     setosa
46           4.8         3.0          1.4         0.3     setosa
48           4.6         3.2          1.4         0.2     setosa
50           5.0         3.3          1.4         0.2     setosa
3            4.7         3.2          1.3         0.2     setosa
17           5.4         3.9          1.3         0.4     setosa
37           5.5         3.5          1.3         0.2     setosa
39           4.4         3.0          1.3         0.2     setosa
41           5.0         3.5          1.3         0.3     setosa
42           4.5         2.3          1.3         0.3     setosa
43           4.4         3.2          1.3         0.2     setosa
15           5.8         4.0          1.2         0.2     setosa
36           5.0         3.2          1.2         0.2     setosa
14           4.3         3.0          1.1         0.1     setosa
23           4.6         3.6          1.0         0.2     setosa
 ```
 ### 1.샘플링
  * 샘플링은 통계용어로서 주어진 값들이 있을 때 그중에서 임의의 개수만큼 값들을 추출하는 작업을 의미한다.  
  비복원추출과 복원 추출이 있으며   
  비복원 추출은 이미 나온 값이 다시 나오지 않고  
  복원 추출은 반대로 이미 나온 값이 다시 나올 확률이 있다.  
  데이터 분석에는 주로 비복원 추출을 많이 사용한다.
```R

```
 ### 2.조합

 ### 데이터 집계

 ### 1.품종별 꽃잎 꽃받침의 폭과 길이의 평균

 ### 2. 품종별 꽃잎 꽃밭짐의 폭과 길이의 표준 편차

 ### 3. 2개의 기준에 대해 다른 열들의 최댓값 구하기

 ### 나무지도

 
## 2023-05-11
### 다중변수 데이터 분석

### 1. 두 변수의 상관관계
```R
    # (1) 데이터 확인
    > head(pressure)
           temperature pressure
        1           0   0.0002
        2          20   0.0012
        3          40   0.0060
        4          60   0.0300
        5          80   0.0900
        6         100   0.2700


    > plot(pressure$temperature,  #x축 데이터
              pressure$pressure,  #y축 데이터
              main='온도와 기압',   # 그래프 제목
              xlab='온도(화씨)',    # x축 레이블
              ylab='기압',         # y축 레이블
            )
```
* 상관관계
x축의 변수의 값이 증가하면 y축 변수의 값이 비례해서 증가하거나 반대로 x축 변수의 값이 증가하면 y축 변수의 값이 비례해서 감소하는 경우 두 변수는 상관관계에 소ㅗㄱ한다.  
두 변수가 어느 정도나 강한 상관관계인지 수치로 나타낸 지표를 상관계수라고 하며 상관계수는 -1에서 1사이의 값을 가진다.  
상관계수가 0인 경우는 두 변수 x,y사이에 상관성을 찾기 어려우며 상관계수가 - 인 경우 x,y가 반비례 하고 음의 상관관계라고 한다. 상관계수가 -1에 가까울수록 강한 음의
상관관계에 있으며 산점도 상의 점들이 직선에 가까워 진다.  
상관계수가 (+)인 경우 x,y가 비례하고 양의 상관관계에 있다고 하며, 상관계수가 1에 가까울수록 x,y는 상관성이 강해진다.
```R
    > head(cars)
            speed dist
        1     4    2
        2     4   10
        3     7    4
        4     7   22
        5     8   16
        6     9   10

    > plot(cars$speed,
      cars$dist,
      main='자동차 속도와 제동거리',
      xlab='속도',
      ylab='제동거리',)

    > cor(cars$speed,cars$dist)
        [1] 0.8068949  #상관계수의 값
```
### 3. 다중변수 사이의 상관관계
* 변수가 3개 이상인 데이터는 변수를 2개씩 짝지어서 상관관계를 분석할 수 있다.
```R
    > st<-data.frame(state.x77)

    > head(st)
                    Population Income Illiteracy Life.Exp Murder HS.Grad Frost   Area
        Alabama          3615   3624        2.1    69.05   15.1    41.3    20  50708
        Alaska            365   6315        1.5    69.31   11.3    66.7   152 566432
        Arizona          2212   4530        1.8    70.55    7.8    58.1    15 113417
        Arkansas         2110   3378        1.9    70.66   10.1    39.9    65  51945
        California      21198   5114        1.1    71.71   10.3    62.6    20 156361
        Colorado         2541   4884        0.7    72.06    6.8    63.9   166 103766    
    > plot(st)
    
    > cor(st)
                Population     Income  Illiteracy    Life.Exp     Murder     HS.Grad
    Population  1.00000000  0.2082276  0.10762237 -0.06805195  0.3436428 -0.09848975
    Income      0.20822756  1.0000000 -0.43707519  0.34025534 -0.2300776  0.61993232
    Illiteracy  0.10762237 -0.4370752  1.00000000 -0.58847793  0.7029752 -0.65718861
    Life.Exp   -0.06805195  0.3402553 -0.58847793  1.00000000 -0.7808458  0.58221620
    Murder      0.34364275 -0.2300776  0.70297520 -0.78084575  1.0000000 -0.48797102
    HS.Grad    -0.09848975  0.6199323 -0.65718861  0.58221620 -0.4879710  1.00000000
    Frost      -0.33215245  0.2262822 -0.67194697  0.26206801 -0.5388834  0.36677970
    Area        0.02254384  0.3633154  0.07726113 -0.10733194  0.2283902  0.33354187
                    Frost        Area
    Population -0.3321525  0.02254384
    Income      0.2262822  0.36331544
    Illiteracy -0.6719470  0.07726113
    Life.Exp    0.2620680 -0.10733194
    Murder     -0.5388834  0.22839021
    HS.Grad     0.3667797  0.33354187
    Frost       1.0000000  0.05922910
    Area        0.0592291  1.00000000
```
### 결측값
현실에서는 데이터 셋처럼 잘 정리된 정보를 얻는 경우가 많지 않다.  
가장 먼저 확보한 데이터를 정제하고 가공해야 비로소 분석에 적합한 데이터를 얻게된다.  
이러한 과정을 데이터 전처리 라고 하며, 데이터 전처리는 전체 분석 과정에서 오랜 시간을 차지하기 때문에  
이를 효과적으로 처리하는 방법을 아는 것이 매우 중요하다.  

결측값이란 데이터의 수집, 저장 과정에서 값을 얻지 못하는 경우 발생하며,결측값은 R에서 NA로 표시된다.
결측값이 섞여 있는 데이터셋은 분석할 때 여러 문제를 일으킨다. 

결측값을 처리하는 방법에는 크게 2가지가 있다.
* 결측값을 제거하거나 제외한 후 분석
* 결측값을 추정하여 적당한 값으로 치환 후 분석
### 1. 벡터의 결측값
```R
    > z<-c(1,2,3,NA,5,NA,8) #결측값이 포함된 벡터

    > sum(z)  #처리되지않음
        [1] NA

    > is.na(z)
        [1] FALSE FALSE FALSE  TRUE FALSE  TRUE FALSE

    > sum(is.na(z))
        [1] 2

    > sum(z, na.rm=TRUE) #NA를 제외하여 계산
        [1] 19


    > z1 <- c(1,2,3,NA,5,NA,8) #결측값 포함 벡터 1

    > z2 <- c(5,8,1,NA,3,NA,7)  #결측값 포함 벡터 2

    > z1[is.na(z1)] <- 0    #NA를 0으로 변환

    > z1
        [1] 1 2 3 0 5 0 8

    > z3 <-as.vector(na.omit(z2)) #NA를 제거하고 새로운 벡터 생성

    > z3
        [1] 5 8 1 3 7
```
### 매트릭스와 데이터 프레임의 결측값
```R
    > x<-iris   #NA를 포함하는 test

    > x[1,2] <- NA; x[1,3]<-NA

    > x[2.3] <- NA; x[3,4]<-NA

    > head(x)
      Sepal.Length Sepal.Width Petal.Length Petal.Width Species
    1          5.1          NA           NA         0.2  setosa
    2          4.9          NA          1.4         0.2  setosa
    3          4.7          NA          1.3          NA  setosa
    4          4.6          NA          1.5         0.2  setosa
    5          5.0          NA          1.4         0.2  setosa
    6          5.4          NA          1.7         0.4  setosa

    #for문을 사용하여 결측값 계산
    > for(i in 1:ncol(x)){
    +   this.na <- is.na(x[,i])
    +   cat(colnames(x)[i], '\t',sum(this.na), '\n')
    + }
        Sepal.Length 	 0 
        Sepal.Width 	 150 
        Petal.Length 	 1 
        Petal.Width 	 1 
        Species 	 0 

    # apply를 사용하여 결측값 계산
    > col_na <- function(y){
    +   return(sum(is.na(y)))
    + }
    > 
    > na_count <-apply(x,2,FUN=col_na)
    > na_count
    Sepal.Length  Sepal.Width Petal.Length  Petal.Width      Species 
            0          150            1            1            0 

```

## 2023-05-04
### 원그래프와 선그래프

### 2. 선 그래프

### 상자그림

### 1. 상자그림의 이해

### 2. 그룹데이터의 상자그림

### 산점도
### 1. 두 변수 사이의 산점도

### 2. 여러 변수들 간의 산점도
### 3. 그룹 정보가 있는 2개 변수의 산점도

### 탐색적 데이터 분석

### 1. 데이터 분석의 절차
### 2. 탐색적 데이터 분석의 이해

### 단일변수 데이터 분석

### 1. 단일변수 범주형 데이터 분석

### 2. 단일변수 수치형 데이터 분석
## 2023-04-27

### 막대 그래프
### 1. 막대그래프 작성의 기초
* 막대그래프는 그룹이나 범주가 정해져 있는 데이터를 시각화 하는데 사용된다  
막대그래프는 그룹별로 집계된 데이터를 표현하는 도구 이기 때문에 먼저 그룹별로 데이터를 집계하는 작업이 필요 하게 된다.

``` R
    > favorite <- c('WINTER','SUMMER','SPRING','SUMMER','SUMMER','FALL','FALL','SUMMER','SPRING','SPRING')

    > favorite
    [1] "WINTER" "SUMMER" "SPRING" "SUMMER" "SUMMER" "FALL"   "FALL"   "SUMMER" "SPRING"
    [10] "SPRING"

    > table(favorite)
    favorite
     FALL SPRING SUMMER WINTER 
        2      3      4      1 

    > ds <- table(favorite)         #도수분포표 저장

    > ds                            #도수분포표 내용 확인
    favorite
     FALL SPRING SUMMER WINTER 
        2      3      4      1 

    > barplot(ds,main='favorite season') #막대 그래프 작성

    > barplot(ds,main='favorite season',col='blue')  #막대의 색 지정 (헥스코드로도 색 설정가능)

    > barplot(ds,main='favorite season',col=('blue','red','green','yellow'))  #막대의 색을 각 각 지정

    > barplot(ds,main='favorite season',col='yellow',horiz=TRUE)    #막대그래프 수평 출력

    > barplot(ds,main='favorite season',col='yellow',names=c('FA','SP','SU','WI'))      #그룹 이름 변경

    > barplot(ds,main='favorite season',col='green',las=2)     #그룹 이름 수직 정렬
```
### 2. 중첩 그룹의 막대그래프
``` R
    > age.A <-c(13709,10974,7979,5000,4250)

    > age.B <-c(17540,29701,36209,33947,24487)

    > age.C <-c(991,2195,5366,12980,19007)

    > ds <- rbind(age.A,age.B,age.C)

    > colnames(ds) <-c('1970','1990','2010','2030','2050')

    > ds
           1970  1990  2010  2030  2050
    age.A 13709 10974  7979  5000  4250
    age.B 17540 29701 36209 33947 24487
    age.C   991  2195  5366 12980 19007

    > barplot(ds,main='인구 추정',col=c('green','blue','yellow')) # 데이터 마다 색 변경

    > barplot(ds,main='인구 추정',col=c('green','blue','yellow'),beside=TRUE) # 데이터 별로 각각의 막대 구성
```

### 3. 막대그래프에 범례 추가

```R
    > barplot(ds,main='인구 추정',col=c('green','blue','yellow'),beside=TRUE,legend.text=T)  #범례 추가

    > par(mfrow=c(1,1),mar=c(5,5,5,7))  #그래프를 표시할 창 설정

    > barplot(ds,main='인구 추정',col=c('green','blue','yellow'),beside=TRUE,legend.text=T,args.lengend =list(x='topright',byy='n'.inset=c(-0.25,0)))

    > par(mfrow=c(1,1),mar=c(5,5,5,7))  #그래프를 표시할 창 설정

    > barplot(ds,main='인구 추정',col=c('green','blue','yellow'),beside=TRUE,legend.text=c('0~14세','15~64세','65세 이상'),args.lengend =list(x='topright',byy='n'.inset=c(-0.25,0)))           #범례 내용 변경

    > par(mfrow=c(1,1),mar=c(5,4,4,2)+0.1)      #그래프 창 설정 해제

```
### 히스토그램 작성
 * 히스토그램은 막대그래프와 는 보기와 비슷하나 그룹이 명시적으로 존재하지 않는 수치형 자료의 분포를 시각화 할때 사용된다
 막대그래프를 그리려면 값의 종류별로 개수를 셀 수 있어야 하는데, 키나 몸무게 등의 수치형 자료는 데이터 내에 값의 종류라는 개념이 없어서
 종류별로 개수를 세기 어렵다.  수치형 자료에서는 구간을 나누고 각각의 구간에 해당하는 값들을 세어서 그래프로 그리는 방식으로 히스토그램이 작성된다.
```R
    > head(cars)
       speed dist
    1     4    2
    2     4   10
    3     7    4
    4     7   22
    5     8   16
    6     9   10
 
    > dist <- cars[,2]      #자동차 제동거리
    
    > dist
    [1]   2  10   4  22  16  10  18  26  34  17  28  14  20  24  28  26  34  34  46  26  36
    [22]  60  80  20  26  54  32  40  32  40  50  42  56  76  84  36  46  68  32  48  52  56
    [43]  64  66  54  70  92  93 120  85

    > hist(dist,                        #data
          main='Histograme for 제동거리',   #제목
          xlab ='제동거리',             # x축 레이블
          ylab ='빈도수',              # y축 레이블
          border='blue',            # 막대 테두리색
          col='green',              # 막대 색
          las=2,                    # x축 글씨 방향(0~3)
          breaks=5)                 # 막대 개수 조절


    > result <- hist(dist,                      #dataß
                main = 'Histogram for 제동거리',      # 제목
                breaks=5)                          #막대 개수 조절
 
    > result
    $breaks
    [1]   0  20  40  60  80 100 120

    $counts
    [1] 10 18 11  6  4  1

    $density
    [1] 0.010 0.018 0.011 0.006 0.004 0.001

    $mids
    [1]  10  30  50  70  90 110

    $xname
    [1] "dist"

    $equidist
    [1] TRUE

    attr(,"class")
    [1] "histogram"

    > freq <- result$counts         #구간별 빈도수 저장

    > names(freq) <- result$breaks[-1]      # 구간값을 이름으로 저장

    > freq                          #구간별 빈도수 출력
        20  40  60  80 100 120 
        10  18  11   6   4   1 

```
### 다른 그래프

### 1. 다중 그래프
 * 그래프창에 어떤 그래프가출력되어 있는 상태에서 또 다른 그래프를 출력하면 이전 그래프는 사라지는데  
 하나의 창에서 여러 개의 그래프를 동시에 출력하여 비교해야할 때가 있다   
 R에서는 그래프 출력창을 가상으로 분할하여 그래프를 출력하는 방법으로도 사용 할 수 있다.
### 2. 그래프를 파일에 저장
 * R에서 만든 그래프를 워드나 파워포인트에서 활용 하기 위에 파일로 저장하여 데이터로 남길 수 있다.
### 원 그래프와 선 그래프
### 1. 원그래프
 * 원그래프는 하나의 원 안에 데이터 값이 차지하는 비율을 넓이로 나타낸 그래프로 도수분포료로부터 쉽게 원
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
* R에서 분석할 데이터에 열이 공백이거나 탭으로 분리된 파일의 경우  
read.table() 함수를 통해 데이터를 읽어 온다.
```R
    > getwd()
        [1] "/Users/junggonlee/Projects/23-Project1-R"      #작업 폴더 확인

    > air <-read.table('airquality.txt',header = T,sep=' ')     #파일 읽기

    > head(air)
            Ozone Solar.R Wind Temp Month Day
        1    41     190  7.4   67     5   1
        2    36     118  8.0   72     5   2
        3    12     149 12.6   74     5   3
        4    18     313 11.5   62     5   4
        5    NA      NA 14.3   56     5   5
        6    28      NA 14.9   66     5   6
```
### 조건문

### 1.if-else
```R
    if(비교 조건){
        참 실행
    } else{
        거짓 실행
    }

    > job.type ='A'

    > if(job.type =='B'){
        bonus <-200
    > }else{
            bonus <-100
        }
    > print(bonus)
        [1] 100
```
### 2.ifelse
 * if-else문을 서술할 때 조건에 따라 선택할 값이 각각 하나일 때는 ifelse를 사용하는것이 편하다
```R
    > a<-10

    > b<-20

    > if(a>b){
         c <- a
      }else{
         c <- b
      }

    > print(c)
        [1] 20

    > a<-10

    > b<-20

    > c<- ifelse(a>b,a,b)

    > print(c)
        [1] 20
```
### 3.if-else 반복
```R
    > score <-85
    
    > if (score >90){
           grade <- 'A'
      } else if(score > 80){
           grade <- 'B'
      }else if(score > 80){
           grade <- 'C'
      }else if(score > 80){
           grade <- 'D'
      }else {
           grade <-"F"
        }
    
    > print(grade)
    [1] "B"
```
### 반복문
* 반복되는 작업에 사용하게되며 for문과 while문이 있다.
### 1.for
```R
    > for(i in 1:5){
        print('*')
        }
    [1] "*"
    [1] "*"
    [1] "*"
    [1] "*"
```
### 2.while
```R
    while(비교 조건){
        반복할 명령문
    }

    > sum <- 0

    > i <- 1

    > while (i <=100) {
        sum <- sum +i
        i <- i+1
      }

    > print(sum)
    [1] 5050
```
### 3.apply() 계열 함수
* 반복 작업의 대상이 매트릭스나 데이터 프레임의 행이나 열인 경우  
for문이나 while문 대신에 apply() 함수를 사용 할 수 있다.
```R
    apply(데이터셋, 행/열 방향 지정, 적용 함수)

    > apply(iris[,1:4],1,mean)
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

    > apply(iris[,1:4],2,mean)
        Sepal.Length  Sepal.Width Petal.Length  Petal.Width 
         5.843333     3.057333     3.758000     1.199333 
```
### 사용자 정의 함수
### 1.사용자 정의 함수의 개념
* 사용자 정의 함수란 사용자가 자주사용하는 R코드를 함수 형태로 저장 해놓고  
그 함수를 호출하여 사용 할 수 있다.
```R
    함수명 <- function(매개변수 목록){
            실행할 명령문(둘)
            return(함수의 실행 결과)
    }
    mymax <- function(x,y){
        num.max <-x
        if(y>x){
            num.max <-y
        }
        return(num.max)
    }

    > mymax <- function(x,y){
       num.max <- x
       if(y>x){
         num.max <-y
       }
       return(num.max)
     }
 
    > mymax(10,15)
    [1] 15
    
    > a<-mymax(20,15)

    > b<-mymax(31,45)

    > print(a+b)
        [1] 65
```
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
    John Tom Mark Jane 
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
