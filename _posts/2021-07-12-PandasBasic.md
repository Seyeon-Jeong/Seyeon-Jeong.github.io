# 1. Pandas의 기초
### (1). Pandas의 기본 자료구조 이해
##### <u>1. 데이터 프레임 (DataFrame)</u>
* 행과 열로 이루어진 표를 의미.
* 데이터분석을 위해 수집, 전처리 등의 과정은 대부분 데이터프레임의 형태로 이루어지는 경우가 많음.

##### <u>2. 시리즈 (Series)</u>
* 데이터프레임의 하위 자료형.
* 1개의 열이 시리즈, 시리즈가 다수 모여 데이터프레임을 형성함.

### (2). 들어가기 전 Pandas에 대하여
* <u>R을 모티브로하여 만든 파이썬에서 사용하는 데이터분석 라이브러리</u>.
* 파이썬에서 정형데이터를 분석할 때 가장 많이 사용하는 라이브러리.
* Excel < Pandas < SQL
* pandas는 1) structred array 2) record array으로 만들어짐.

### 1.1 import 하기


```python
import pandas as pd # Pandas를 사용하기 위해서는 pandas를 설치한 후에 import를 해야함.
import seaborn as sns # seaborn은 Python 시각화에 가장 많이 사용되는 라이브러리 중에 하나임.
```

### 1.2 데이터 불러오기


```python
tips = sns.load_dataset('tips') 
# 실습에 사용할 데이터는 tips 데이터. -> tips라는 데이터를 tips라는 이름으로 저장.
# tips 데이터는 seaborn에 내장되어 있어 위 명령으로 불러올 수 있음.
```


```python
tips 
# 불러온 데이터 확인.
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>239</th>
      <td>29.03</td>
      <td>5.92</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>240</th>
      <td>27.18</td>
      <td>2.00</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>241</th>
      <td>22.67</td>
      <td>2.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>242</th>
      <td>17.82</td>
      <td>1.75</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>243</th>
      <td>18.78</td>
      <td>3.00</td>
      <td>Female</td>
      <td>No</td>
      <td>Thur</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 7 columns</p>
</div>



### 1.3 불러온 데이터 살펴보기

##### type() 함수 = 데이터 타입을 확인할 수 있는 함수


```python
type(tips)
# tips의 타입은 DataFrame.
```




    pandas.core.frame.DataFrame



##### index 함수 = 데이터 프레임의 내용을 행 기준으로 표시


```python
tips.index
# tips 는 행을 기준으로 0번부터 시작해 하나씩 늘어나 244번까지 있음
```




    RangeIndex(start=0, stop=244, step=1)



##### columns 함수 = 제목에 있는 값을 추출


```python
tips.columns
# 제목 줄은 column이라 함.
```




    Index(['total_bill', 'tip', 'sex', 'smoker', 'day', 'time', 'size'], dtype='object')



##### (데이터명)['데이터 제목명'] = 데이터의 제목들 중 특정 제목의 속성값들만 추출


```python
tips['tip'] 
# 제목에 있는 항목 중 tip만 추출.
```




    0      1.01
    1      1.66
    2      3.50
    3      3.31
    4      3.61
           ... 
    239    5.92
    240    2.00
    241    2.00
    242    1.75
    243    3.00
    Name: tip, Length: 244, dtype: float64




```python
type(tips['tip']) 
# 위 tip의 타입은 시리즈
```




    pandas.core.series.Series



##### loc[] 함수 = 인덱스 기준으로 행 데이터 읽는 함수


```python
type(tips.loc[0])
# tips 자료의 0번 인덱스의 타입은 시리즈.
```




    pandas.core.series.Series



##### info() 함수 = 데이터에 대한 전반적인 정보 나타냄


```python
tips.info()
# tips를 구성하는 행과 열의 크기, 컬럼명, 컬럼을 구성하는 값의 자료형 등을 출력함.
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 244 entries, 0 to 243
    Data columns (total 7 columns):
     #   Column      Non-Null Count  Dtype   
    ---  ------      --------------  -----   
     0   total_bill  244 non-null    float64 
     1   tip         244 non-null    float64 
     2   sex         244 non-null    category
     3   smoker      244 non-null    category
     4   day         244 non-null    category
     5   time        244 non-null    category
     6   size        244 non-null    int64   
    dtypes: category(4), float64(2), int64(1)
    memory usage: 7.4 KB
    

##### dtypes 함수 = 각 제목 속성값들의 데이터형 확인


```python
tips.dtypes
```




    total_bill     float64
    tip            float64
    sex           category
    smoker        category
    day           category
    time          category
    size             int64
    dtype: object



##### shape 함수 = 데이터의 (행,열) 크기 확인


```python
tips.shape
# tips 자료에는 244개의 행, 7개의 열 존재.
```




    (244, 7)



##### values 함수 = 행 기준으로 모든 속성값 한 줄에 하나씩 추출


```python
tips.values
```




    array([[16.99, 1.01, 'Female', ..., 'Sun', 'Dinner', 2],
           [10.34, 1.66, 'Male', ..., 'Sun', 'Dinner', 3],
           [21.01, 3.5, 'Male', ..., 'Sun', 'Dinner', 3],
           ...,
           [22.67, 2.0, 'Male', ..., 'Sat', 'Dinner', 2],
           [17.82, 1.75, 'Male', ..., 'Sat', 'Dinner', 2],
           [18.78, 3.0, 'Female', ..., 'Thur', 'Dinner', 2]], dtype=object)



##### <u>values = .to_numpy()</u>


```python
tips.to_numpy()
# tips.values()와 같음
```




    array([[16.99, 1.01, 'Female', ..., 'Sun', 'Dinner', 2],
           [10.34, 1.66, 'Male', ..., 'Sun', 'Dinner', 3],
           [21.01, 3.5, 'Male', ..., 'Sun', 'Dinner', 3],
           ...,
           [22.67, 2.0, 'Male', ..., 'Sat', 'Dinner', 2],
           [17.82, 1.75, 'Male', ..., 'Sat', 'Dinner', 2],
           [18.78, 3.0, 'Female', ..., 'Thur', 'Dinner', 2]], dtype=object)



##### values[행,열] = 특정 행, 열에 속하는 속성값만 추출


```python
tips.values[0,0]
#  행의 0 = 0, 열의 0 = total_bill
# total_bill 의 0번 인덱스는 16.99
```




    16.99



##### axes = 가로축과 세로축을 나타내는 목록을 각각 변환
##### axes=0 (index) => 행에 따라 동작, 각 열의 모든 행에 대해 작용함
##### axes = 1 (columns) => 열에 따라 동작, 각 행의 모든 열에 대해 작동함


```python
tips.axes
# tips.index, tips.columns
```




    [RangeIndex(start=0, stop=244, step=1),
     Index(['total_bill', 'tip', 'sex', 'smoker', 'day', 'time', 'size'], dtype='object')]



##### size = 불러온 데이터 프레임 내의 요소의 수 알려줌


```python
tips.size
```




    1708



##### memory_usage() = 각 칼럼의 메모리 사용량을 바이트 단위로 알려줌


```python
tips.memory_usage()
```




    Index          128
    total_bill    1952
    tip           1952
    sex            368
    smoker         368
    day            448
    time           368
    size          1952
    dtype: int64



### 1.4 Structured array와 Record array 의 차이

##### structured array
- Numpy는 C의 구조체로 어우러진 배열에 해당하는 structured array 지원


```python
tips['tip'] # Structured array
```




    0      1.01
    1      1.66
    2      3.50
    3      3.31
    4      3.61
           ... 
    239    5.92
    240    2.00
    241    2.00
    242    1.75
    243    3.00
    Name: tip, Length: 244, dtype: float64



##### record array
- 가장 단순하게 레코드 배열에 해당함


```python
tips.tip # record array
```




    0      1.01
    1      1.66
    2      3.50
    3      3.31
    4      3.61
           ... 
    239    5.92
    240    2.00
    241    2.00
    242    1.75
    243    3.00
    Name: tip, Length: 244, dtype: float64




```python
tips.day == 'Fri' 
# 특정 제목의 속성과 지정한 값이 같으면 True, 같지 않으면 False로 뽑을 수 있음
```




    0      False
    1      False
    2      False
    3      False
    4      False
           ...  
    239    False
    240    False
    241    False
    242    False
    243    False
    Name: day, Length: 244, dtype: bool



### 1.5 fancy indexing
= 정수나 불린(Boolean) 값을 가지는 다른 numpy 배열로 배열을 인덱싱 할 수 있는 기능

##### fancy indexing 1차원


```python
tips[['tip']]
# 제목이 tip인 배열만 가져오기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tip</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.66</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.50</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3.31</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3.61</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>239</th>
      <td>5.92</td>
    </tr>
    <tr>
      <th>240</th>
      <td>2.00</td>
    </tr>
    <tr>
      <th>241</th>
      <td>2.00</td>
    </tr>
    <tr>
      <th>242</th>
      <td>1.75</td>
    </tr>
    <tr>
      <th>243</th>
      <td>3.00</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 1 columns</p>
</div>



##### fancy indexing 2차원


```python
tips[['tip', 'day']]
# 제목이 tip과 day인 배열만 가져와 인덱싱하기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tip</th>
      <th>day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.01</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.66</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.50</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3.31</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3.61</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>239</th>
      <td>5.92</td>
      <td>Sat</td>
    </tr>
    <tr>
      <th>240</th>
      <td>2.00</td>
      <td>Sat</td>
    </tr>
    <tr>
      <th>241</th>
      <td>2.00</td>
      <td>Sat</td>
    </tr>
    <tr>
      <th>242</th>
      <td>1.75</td>
      <td>Sat</td>
    </tr>
    <tr>
      <th>243</th>
      <td>3.00</td>
      <td>Thur</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 2 columns</p>
</div>




```python
tips[['day', 'tip']]
# 순서를 바꿔 인덱싱 가능
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>day</th>
      <th>tip</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sun</td>
      <td>1.01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sun</td>
      <td>1.66</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Sun</td>
      <td>3.50</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Sun</td>
      <td>3.31</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sun</td>
      <td>3.61</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>239</th>
      <td>Sat</td>
      <td>5.92</td>
    </tr>
    <tr>
      <th>240</th>
      <td>Sat</td>
      <td>2.00</td>
    </tr>
    <tr>
      <th>241</th>
      <td>Sat</td>
      <td>2.00</td>
    </tr>
    <tr>
      <th>242</th>
      <td>Sat</td>
      <td>1.75</td>
    </tr>
    <tr>
      <th>243</th>
      <td>Thur</td>
      <td>3.00</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 2 columns</p>
</div>



##### Boolean indexing


```python
tips[tips.day == 'Sun']
# 데이터프레임 제목 중 day가 Sun인 배열들만 뽑아 인덱싱
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>186</th>
      <td>20.90</td>
      <td>3.50</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>187</th>
      <td>30.46</td>
      <td>2.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>5</td>
    </tr>
    <tr>
      <th>188</th>
      <td>18.15</td>
      <td>3.50</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>189</th>
      <td>23.10</td>
      <td>4.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>190</th>
      <td>15.69</td>
      <td>1.50</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>76 rows × 7 columns</p>
</div>



##### select_dtypes() = object형 데이터와 비object형(숫자형) 데이터를 구분해서 호출해주는 함수


```python
tips.select_dtypes(exclude = 'int64')
# 데이터프레임 속성 값의 자료형이 64비트 정수가 아닌 배열 값들만 뽑아 인덱싱
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>239</th>
      <td>29.03</td>
      <td>5.92</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>240</th>
      <td>27.18</td>
      <td>2.00</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>241</th>
      <td>22.67</td>
      <td>2.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>242</th>
      <td>17.82</td>
      <td>1.75</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>243</th>
      <td>18.78</td>
      <td>3.00</td>
      <td>Female</td>
      <td>No</td>
      <td>Thur</td>
      <td>Dinner</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 6 columns</p>
</div>



##### regex = 특정 조건을 만족하는 변수만 뽑기


```python
tips.filter(regex='^t') 
# ^t = t로 시작하는 문자열
# t로 시작하는 제목줄 변수들만 뽑기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>239</th>
      <td>29.03</td>
      <td>5.92</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>240</th>
      <td>27.18</td>
      <td>2.00</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>241</th>
      <td>22.67</td>
      <td>2.00</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>242</th>
      <td>17.82</td>
      <td>1.75</td>
      <td>Dinner</td>
    </tr>
    <tr>
      <th>243</th>
      <td>18.78</td>
      <td>3.00</td>
      <td>Dinner</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 3 columns</p>
</div>



### 1.6 set_index()로 index 설정 바꾸기

##### set_index() = 데이터 프레임을 먼저 불러온 후에, 특정 열을 인덱스로 설정시 사용


```python
tips2 = tips.set_index('time')
# 원래 있던 indew의 0,1,2,... 대신 time이란 특정 열로 변경
```


```python
tips2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>size</th>
    </tr>
    <tr>
      <th>time</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Dinner</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>29.03</td>
      <td>5.92</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>27.18</td>
      <td>2.00</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>22.67</td>
      <td>2.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>17.82</td>
      <td>1.75</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>18.78</td>
      <td>3.00</td>
      <td>Female</td>
      <td>No</td>
      <td>Thur</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>244 rows × 6 columns</p>
</div>



### 1.7 set_index()로 index 설정 바뀐 데이터프레임을 iloc[]과 loc[]으로 살펴보기

#### <u>iloc과 loc의 차이</u>
##### (1) iloc 
- index를 활용해 위치 지정 방법
- DataFrame.iloc[index_index,column_index]

##### (2) loc
- index를 활용하지 않고, 직접 index 및 column명을 통해 지정하는 방법
- DataFrame.loc[index_name, column_name]


```python
tips2.iloc[-1]
# 맨 아래부터 첫 번째 행 추출
```




    total_bill     18.78
    tip              3.0
    sex           Female
    smoker            No
    day             Thur
    size               2
    Name: Dinner, dtype: object




```python
tips2.iloc[3:]
# 위부터 4번째부터 끝까지 행 추출
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>size</th>
    </tr>
    <tr>
      <th>time</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Dinner</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>4</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>25.29</td>
      <td>4.71</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>4</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>8.77</td>
      <td>2.00</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>26.88</td>
      <td>3.12</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>29.03</td>
      <td>5.92</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>27.18</td>
      <td>2.00</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>22.67</td>
      <td>2.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>17.82</td>
      <td>1.75</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>18.78</td>
      <td>3.00</td>
      <td>Female</td>
      <td>No</td>
      <td>Thur</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>241 rows × 6 columns</p>
</div>




```python
tips2.loc['Dinner']
# time 열의 값들 중 Dinner인 값들만 뽑기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>size</th>
    </tr>
    <tr>
      <th>time</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Dinner</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>29.03</td>
      <td>5.92</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>3</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>27.18</td>
      <td>2.00</td>
      <td>Female</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>22.67</td>
      <td>2.00</td>
      <td>Male</td>
      <td>Yes</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>17.82</td>
      <td>1.75</td>
      <td>Male</td>
      <td>No</td>
      <td>Sat</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Dinner</th>
      <td>18.78</td>
      <td>3.00</td>
      <td>Female</td>
      <td>No</td>
      <td>Thur</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
<p>176 rows × 6 columns</p>
</div>



##### iloc과 loc 차이 비교 (1)


```python
tips.iloc[0:3]
# 0번 인덱스 행부터 2번 인덱스 행까지 뽑기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>




```python
tips.loc[0:3] 
# 0번 인덱스 행부터 3번 인덱스 행까지 뽑기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



##### iloc과 loc 차이 비교 (2)


```python
tips.iloc[0:3, 1:4]
# 0번 인덱스 행부터 2번 인덱스 행의 2번째 열부터 4번째 열까지의 값만 뽑기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
    </tr>
  </tbody>
</table>
</div>




```python
tips.loc[0:3, 'tip':'day']
# 0번 인덱스 행부터 3번 인덱스 행의 'tip' 열부터 'day'열까지의 값만 뽑기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
    </tr>
  </tbody>
</table>
</div>



##### iloc[] 좀 더 살펴보기


```python
tips.iloc[[0,3]]
# 0번째 index와 3번째 index 행 값들만 뽑기
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
tips.iloc[[3,0]]
# 순서 바꾸는 것 가능
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



##### iloc[]과 fast indexing인 iat[] 비교

##### iat[] 
* iloc 메서드와 동일하게 위치 정수로 데이터에 접근하는 메서드
* 단, 하나의 스칼라 값에만 접근 가능
* Series.iat[index_int]
* DataFrame.iat[index_int, column_int]


```python
tips.iloc[1,3]
# 1번째 index와 4번째 열 값
```




    'No'




```python
tips.at[1, 'smoker']
# 위 아래 코드와 같은 내용
```




    'No'




```python
tips.iat[1,3]
# 1번째 index와 4번째 열 값
```




    'No'



##### .iloc[]와 .iat[] 속도 차이


```python
%timeit tips.iloc[1,3]
```

    30.1 µs ± 3.34 µs per loop (mean ± std. dev. of 7 runs, 10000 loops each)
    


```python
%timeit tips.iat[1,3]
```

    24.6 µs ± 404 ns per loop (mean ± std. dev. of 7 runs, 10000 loops each)
    

##### .iloc[]와 .iat[] 중 .iat[]이 더 빠르다는 것을 알 수 있음

### 1.8 NaN 으로 나타나는 값을 특정 값으로 변경해주기


```python
tips.day
```




    0       Sun
    1       Sun
    2       Sun
    3       Sun
    4       Sun
           ... 
    239     Sat
    240     Sat
    241     Sat
    242     Sat
    243    Thur
    Name: day, Length: 244, dtype: category
    Categories (4, object): ['Thur', 'Fri', 'Sat', 'Sun']




```python
tips.day.where(tips.day=='Sat')
# tips 자료 중 day가 Sat인 값만 표시 -> Sat이 아닌 값들은 NaN으로 표기
```




    0      NaN
    1      NaN
    2      NaN
    3      NaN
    4      NaN
          ... 
    239    Sat
    240    Sat
    241    Sat
    242    Sat
    243    NaN
    Name: day, Length: 244, dtype: category
    Categories (4, object): ['Thur', 'Fri', 'Sat', 'Sun']




```python
tips.day.where(tips.day=='Sat', 'Thur') 
# tips 자료 중 day가 Sat이면 Sat, 아니면 Thur로 표기
```




    0      Thur
    1      Thur
    2      Thur
    3      Thur
    4      Thur
           ... 
    239     Sat
    240     Sat
    241     Sat
    242     Sat
    243    Thur
    Name: day, Length: 244, dtype: category
    Categories (4, object): ['Thur', 'Fri', 'Sat', 'Sun']




```python

```
