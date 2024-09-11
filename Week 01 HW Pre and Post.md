```python
import pandas as pd
url = "https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-05-05/villagers.csv"
df = pd.read_csv(url)
print(df)
df.isna().sum()
```

         row_n        id      name  gender    species birthday personality  \
    0        2   admiral   Admiral    male       bird     1-27      cranky   
    1        3   agent-s   Agent S  female   squirrel      7-2       peppy   
    2        4     agnes     Agnes  female        pig     4-21        uchi   
    3        6        al        Al    male    gorilla    10-18        lazy   
    4        7   alfonso   Alfonso    male  alligator      6-9        lazy   
    ..     ...       ...       ...     ...        ...      ...         ...   
    386    475    winnie    Winnie  female      horse     1-31       peppy   
    387    477  wolfgang  Wolfgang    male       wolf    11-25      cranky   
    388    480      yuka      Yuka  female      koala     7-20      snooty   
    389    481      zell      Zell    male       deer      6-7        smug   
    390    483    zucker    Zucker    male    octopus      3-8        lazy   
    
                    song    phrase            full_id  \
    0         Steep Hill   aye aye   villager-admiral   
    1            DJ K.K.  sidekick   villager-agent-s   
    2         K.K. House   snuffle     villager-agnes   
    3         Steep Hill   Ayyeeee        villager-al   
    4        Forest Life  it'sa me   villager-alfonso   
    ..               ...       ...                ...   
    386         My Place    hay-OK    villager-winnie   
    387        K.K. Song   snarrrl  villager-wolfgang   
    388     Soulful K.K.   tsk tsk      villager-yuka   
    389         K.K. D&B     pronk      villager-zell   
    390  Spring Blossoms     bloop    villager-zucker   
    
                                                       url  
    0    https://villagerdb.com/images/villagers/thumb/...  
    1    https://villagerdb.com/images/villagers/thumb/...  
    2    https://villagerdb.com/images/villagers/thumb/...  
    3    https://villagerdb.com/images/villagers/thumb/...  
    4    https://villagerdb.com/images/villagers/thumb/...  
    ..                                                 ...  
    386  https://villagerdb.com/images/villagers/thumb/...  
    387  https://villagerdb.com/images/villagers/thumb/...  
    388  https://villagerdb.com/images/villagers/thumb/...  
    389  https://villagerdb.com/images/villagers/thumb/...  
    390  https://villagerdb.com/images/villagers/thumb/...  
    
    [391 rows x 11 columns]





    row_n           0
    id              1
    name            0
    gender          0
    species         0
    birthday        0
    personality     0
    song           11
    phrase          0
    full_id         0
    url             0
    dtype: int64




```python
dimensions = df.shape
print(f"The dataset contains {dimensions[0]} observations (rows) and {dimensions[1]} variables (columns).")

```

    The dataset contains 391 observations (rows) and 11 variables (columns).



```python
df.isna().sum(axis=1)
```




    0      0
    1      0
    2      0
    3      0
    4      0
          ..
    386    0
    387    0
    388    0
    389    0
    390    0
    Length: 391, dtype: int64




```python
# Variables are the columns of the dataset (name, gender, species, etc.), while observations are the rows of
# the dataset (in this case, the individual villagers of Animal Crossing)
```


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 391 entries, 0 to 390
    Data columns (total 11 columns):
     #   Column       Non-Null Count  Dtype 
    ---  ------       --------------  ----- 
     0   row_n        391 non-null    int64 
     1   id           390 non-null    object
     2   name         391 non-null    object
     3   gender       391 non-null    object
     4   species      391 non-null    object
     5   birthday     391 non-null    object
     6   personality  391 non-null    object
     7   song         380 non-null    object
     8   phrase       391 non-null    object
     9   full_id      391 non-null    object
     10  url          391 non-null    object
    dtypes: int64(1), object(10)
    memory usage: 33.7+ KB



```python
df.describe()
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
      <th>row_n</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>391.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>239.902813</td>
    </tr>
    <tr>
      <th>std</th>
      <td>140.702672</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>117.500000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>240.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>363.500000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>483.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe(include='all')
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
      <th>row_n</th>
      <th>id</th>
      <th>name</th>
      <th>gender</th>
      <th>species</th>
      <th>birthday</th>
      <th>personality</th>
      <th>song</th>
      <th>phrase</th>
      <th>full_id</th>
      <th>url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>391.000000</td>
      <td>390</td>
      <td>391</td>
      <td>391</td>
      <td>391</td>
      <td>391</td>
      <td>391</td>
      <td>380</td>
      <td>391</td>
      <td>391</td>
      <td>391</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>NaN</td>
      <td>390</td>
      <td>391</td>
      <td>2</td>
      <td>35</td>
      <td>361</td>
      <td>8</td>
      <td>92</td>
      <td>388</td>
      <td>391</td>
      <td>391</td>
    </tr>
    <tr>
      <th>top</th>
      <td>NaN</td>
      <td>admiral</td>
      <td>Admiral</td>
      <td>male</td>
      <td>cat</td>
      <td>1-27</td>
      <td>lazy</td>
      <td>K.K. Country</td>
      <td>wee one</td>
      <td>villager-admiral</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>NaN</td>
      <td>1</td>
      <td>1</td>
      <td>204</td>
      <td>23</td>
      <td>2</td>
      <td>60</td>
      <td>10</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>239.902813</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>140.702672</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>117.500000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>240.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>363.500000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>483.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.shape
```




    (391, 11)




```python
# There is no difference between the number in the "count" compared to df.shape or df.describe
```


```python
# A "method" such as df.describe() involves complex computations that are performed and yield a summarisation 
# of statistical information (such as metrics like mean, min, max). As the function involves complex processes,
# a () is present.
```


```python
# An "attribute" such as df.shape is able to provide information without the use of complex computation,
# and thus do not require the use of ().
```


```python
https://chatgpt.com/share/935105c9-6bee-4274-878a-15bdfec29be9 
```


```python
# The df.describe() functions prints the 'count', 'mean', 'std', 'min', '25%', '50%', '75%', and 'max' summary 
# statistics for each variable analysed. 
# The count refers to the number of entries in each column, which is useful for identifying missing values
# The mean refers to the average values in each column 
# The STD refers to the standard deviation of the values - amount of dispersion from the mean
# The min refers to the minimum value in each column
# 25% refers to the point of the first quartile of data in the column
# 50% refers to the median point of the data in the column
# 75% refers to the point of the third quartile of data in the column
# The max refers to the maximum value in each column
```


```python
# df.dropna() might be preferred over using del df['col'] in the cases in which you are trying to remove certain rows/columns
# containing missing data - ex. if in a dataframe, there is a row that is missing data for multiple columns, you may want to
# use the df.dropna() function to remove the row from the dataframe
```


```python
# del df['col'] might be preferred over using df.dropna() in the cases in which you are trying to remove an entire column from
# a dataframe, regardless of whether or not the column has missing values - ex. if in a dataset, there is an irrelevant column,
# you may use del df['col'] to delete that specific column from the dataframe
```


```python
# It is possible that the application of the functin del df['col'] before df.dropna() may be important, as if df.dropna() was 
# used prior to del df['col'], it is possible that the missing values deleted by the df.dropna() function may cause rows to be
# deleted, which may contain important values for other columns.
```


```python
df.describe()
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
      <th>row_n</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>391.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>239.902813</td>
    </tr>
    <tr>
      <th>std</th>
      <td>140.702672</td>
    </tr>
    <tr>
      <th>min</th>
      <td>2.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>117.500000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>240.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>363.500000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>483.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe()
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
      <th>survived</th>
      <th>pclass</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>714.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
      <td>891.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.383838</td>
      <td>2.308642</td>
      <td>29.699118</td>
      <td>0.523008</td>
      <td>0.381594</td>
      <td>32.204208</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.486592</td>
      <td>0.836071</td>
      <td>14.526497</td>
      <td>1.102743</td>
      <td>0.806057</td>
      <td>49.693429</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.420000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.000000</td>
      <td>2.000000</td>
      <td>20.125000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>7.910400</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.000000</td>
      <td>3.000000</td>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>14.454200</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>38.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>31.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>1.000000</td>
      <td>3.000000</td>
      <td>80.000000</td>
      <td>8.000000</td>
      <td>6.000000</td>
      <td>512.329200</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.dropna()
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
      <th>row_n</th>
      <th>id</th>
      <th>name</th>
      <th>gender</th>
      <th>species</th>
      <th>birthday</th>
      <th>personality</th>
      <th>song</th>
      <th>phrase</th>
      <th>full_id</th>
      <th>url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>admiral</td>
      <td>Admiral</td>
      <td>male</td>
      <td>bird</td>
      <td>1-27</td>
      <td>cranky</td>
      <td>Steep Hill</td>
      <td>aye aye</td>
      <td>villager-admiral</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3</td>
      <td>agent-s</td>
      <td>Agent S</td>
      <td>female</td>
      <td>squirrel</td>
      <td>7-2</td>
      <td>peppy</td>
      <td>DJ K.K.</td>
      <td>sidekick</td>
      <td>villager-agent-s</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>agnes</td>
      <td>Agnes</td>
      <td>female</td>
      <td>pig</td>
      <td>4-21</td>
      <td>uchi</td>
      <td>K.K. House</td>
      <td>snuffle</td>
      <td>villager-agnes</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6</td>
      <td>al</td>
      <td>Al</td>
      <td>male</td>
      <td>gorilla</td>
      <td>10-18</td>
      <td>lazy</td>
      <td>Steep Hill</td>
      <td>Ayyeeee</td>
      <td>villager-al</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>7</td>
      <td>alfonso</td>
      <td>Alfonso</td>
      <td>male</td>
      <td>alligator</td>
      <td>6-9</td>
      <td>lazy</td>
      <td>Forest Life</td>
      <td>it'sa me</td>
      <td>villager-alfonso</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>386</th>
      <td>475</td>
      <td>winnie</td>
      <td>Winnie</td>
      <td>female</td>
      <td>horse</td>
      <td>1-31</td>
      <td>peppy</td>
      <td>My Place</td>
      <td>hay-OK</td>
      <td>villager-winnie</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>387</th>
      <td>477</td>
      <td>wolfgang</td>
      <td>Wolfgang</td>
      <td>male</td>
      <td>wolf</td>
      <td>11-25</td>
      <td>cranky</td>
      <td>K.K. Song</td>
      <td>snarrrl</td>
      <td>villager-wolfgang</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>388</th>
      <td>480</td>
      <td>yuka</td>
      <td>Yuka</td>
      <td>female</td>
      <td>koala</td>
      <td>7-20</td>
      <td>snooty</td>
      <td>Soulful K.K.</td>
      <td>tsk tsk</td>
      <td>villager-yuka</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>389</th>
      <td>481</td>
      <td>zell</td>
      <td>Zell</td>
      <td>male</td>
      <td>deer</td>
      <td>6-7</td>
      <td>smug</td>
      <td>K.K. D&amp;B</td>
      <td>pronk</td>
      <td>villager-zell</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
    <tr>
      <th>390</th>
      <td>483</td>
      <td>zucker</td>
      <td>Zucker</td>
      <td>male</td>
      <td>octopus</td>
      <td>3-8</td>
      <td>lazy</td>
      <td>Spring Blossoms</td>
      <td>bloop</td>
      <td>villager-zucker</td>
      <td>https://villagerdb.com/images/villagers/thumb/...</td>
    </tr>
  </tbody>
</table>
<p>379 rows × 11 columns</p>
</div>




```python
# as there were no unnecessary columns that needed to be removed in its entirety from the dataframe, I chose to use the function
# df.dropna() instead to remove the missing values - which resulted in 12 rows being removed.
```


```python
import pandas as pd
url = "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanic.csv"
df = pd.read_csv(url)
print(df)
```

         survived  pclass     sex   age  sibsp  parch     fare embarked   class  \
    0           0       3    male  22.0      1      0   7.2500        S   Third   
    1           1       1  female  38.0      1      0  71.2833        C   First   
    2           1       3  female  26.0      0      0   7.9250        S   Third   
    3           1       1  female  35.0      1      0  53.1000        S   First   
    4           0       3    male  35.0      0      0   8.0500        S   Third   
    ..        ...     ...     ...   ...    ...    ...      ...      ...     ...   
    886         0       2    male  27.0      0      0  13.0000        S  Second   
    887         1       1  female  19.0      0      0  30.0000        S   First   
    888         0       3  female   NaN      1      2  23.4500        S   Third   
    889         1       1    male  26.0      0      0  30.0000        C   First   
    890         0       3    male  32.0      0      0   7.7500        Q   Third   
    
           who  adult_male deck  embark_town alive  alone  
    0      man        True  NaN  Southampton    no  False  
    1    woman       False    C    Cherbourg   yes  False  
    2    woman       False  NaN  Southampton   yes   True  
    3    woman       False    C  Southampton   yes  False  
    4      man        True  NaN  Southampton    no   True  
    ..     ...         ...  ...          ...   ...    ...  
    886    man        True  NaN  Southampton    no   True  
    887  woman       False    B  Southampton   yes   True  
    888  woman       False  NaN  Southampton    no  False  
    889    man        True    C    Cherbourg   yes   True  
    890    man        True  NaN   Queenstown    no   True  
    
    [891 rows x 15 columns]



```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 15 columns):
     #   Column       Non-Null Count  Dtype  
    ---  ------       --------------  -----  
     0   survived     891 non-null    int64  
     1   pclass       891 non-null    int64  
     2   sex          891 non-null    object 
     3   age          714 non-null    float64
     4   sibsp        891 non-null    int64  
     5   parch        891 non-null    int64  
     6   fare         891 non-null    float64
     7   embarked     889 non-null    object 
     8   class        891 non-null    object 
     9   who          891 non-null    object 
     10  adult_male   891 non-null    bool   
     11  deck         203 non-null    object 
     12  embark_town  889 non-null    object 
     13  alive        891 non-null    object 
     14  alone        891 non-null    bool   
    dtypes: bool(2), float64(2), int64(4), object(7)
    memory usage: 92.4+ KB



```python
df.groupby("survived")["pclass"].describe()
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
      <th>count</th>
      <th>mean</th>
      <th>std</th>
      <th>min</th>
      <th>25%</th>
      <th>50%</th>
      <th>75%</th>
      <th>max</th>
    </tr>
    <tr>
      <th>survived</th>
      <th></th>
      <th></th>
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
      <th>0</th>
      <td>549.0</td>
      <td>2.531876</td>
      <td>0.735805</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>342.0</td>
      <td>1.950292</td>
      <td>0.863321</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>3.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# The function df.groupby("col1")["col2"].describe() groups the dataframe by "col1" - in this case the "survived" and selects
# the second column "col2" - "pclass" to be analysed, and prints the statistics for "pclass" within the groups of "survived"
```


```python
import pandas as pd
url = "https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2020/2020-05-05/villagers.csv"
df = pd.read_csv(url)
print(df)
```

         row_n        id      name  gender    species birthday personality  \
    0        2   admiral   Admiral    male       bird     1-27      cranky   
    1        3   agent-s   Agent S  female   squirrel      7-2       peppy   
    2        4     agnes     Agnes  female        pig     4-21        uchi   
    3        6        al        Al    male    gorilla    10-18        lazy   
    4        7   alfonso   Alfonso    male  alligator      6-9        lazy   
    ..     ...       ...       ...     ...        ...      ...         ...   
    386    475    winnie    Winnie  female      horse     1-31       peppy   
    387    477  wolfgang  Wolfgang    male       wolf    11-25      cranky   
    388    480      yuka      Yuka  female      koala     7-20      snooty   
    389    481      zell      Zell    male       deer      6-7        smug   
    390    483    zucker    Zucker    male    octopus      3-8        lazy   
    
                    song    phrase            full_id  \
    0         Steep Hill   aye aye   villager-admiral   
    1            DJ K.K.  sidekick   villager-agent-s   
    2         K.K. House   snuffle     villager-agnes   
    3         Steep Hill   Ayyeeee        villager-al   
    4        Forest Life  it'sa me   villager-alfonso   
    ..               ...       ...                ...   
    386         My Place    hay-OK    villager-winnie   
    387        K.K. Song   snarrrl  villager-wolfgang   
    388     Soulful K.K.   tsk tsk      villager-yuka   
    389         K.K. D&B     pronk      villager-zell   
    390  Spring Blossoms     bloop    villager-zucker   
    
                                                       url  
    0    https://villagerdb.com/images/villagers/thumb/...  
    1    https://villagerdb.com/images/villagers/thumb/...  
    2    https://villagerdb.com/images/villagers/thumb/...  
    3    https://villagerdb.com/images/villagers/thumb/...  
    4    https://villagerdb.com/images/villagers/thumb/...  
    ..                                                 ...  
    386  https://villagerdb.com/images/villagers/thumb/...  
    387  https://villagerdb.com/images/villagers/thumb/...  
    388  https://villagerdb.com/images/villagers/thumb/...  
    389  https://villagerdb.com/images/villagers/thumb/...  
    390  https://villagerdb.com/images/villagers/thumb/...  
    
    [391 rows x 11 columns]



```python
df.groupby("gender")["species"].describe()
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
      <th>count</th>
      <th>unique</th>
      <th>top</th>
      <th>freq</th>
    </tr>
    <tr>
      <th>gender</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>female</th>
      <td>187</td>
      <td>33</td>
      <td>cat</td>
      <td>14</td>
    </tr>
    <tr>
      <th>male</th>
      <td>204</td>
      <td>34</td>
      <td>frog</td>
      <td>13</td>
    </tr>
  </tbody>
</table>
</div>




```python
# In the Animal Crossing example shown above, the function df.groupby("col1")["col2"].describe() was used with
# "col1" being replaced by "gender" and "col2" with "species", which caused the dataframe to be grouped by gender,
# and then species was analysed - which printed the count of male and female characters, along with the top species
# and the frequency in the dataframe.
```


```python
# The function df.describe() would have different values than df.groupby because the counts themselves are fundamentally
# different. While df.describe() prints out the amount of overall complete data present for each variable, df.groupby
# analyses "col2" only, within the confines of the group defined by "col1", printing the complete data of "col2" 
# in said context.
```


```python
url = "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanic.csv"
df = pd.read_csv(url)
print(df)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Cell In[1], line 2
          1 url = "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanic.csv"
    ----> 2 df = pd.read_csv(url)
          3 print(df)


    NameError: name 'pd' is not defined



```python
# ChatGPT was much more efficient and helpful in realising the problem for the situation above in comparison to Google,
# as it instead immediately pointed out the error and the code necessary to resolve it, which Google did not.
```


```python
import pandas as pd
url = "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanics.csv"
df = pd.read_csv(url)
print(df)
```


    ---------------------------------------------------------------------------

    HTTPError                                 Traceback (most recent call last)

    Cell In[2], line 3
          1 import pandas as pd
          2 url = "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanics.csv"
    ----> 3 df = pd.read_csv(url)
          4 print(df)


    File /opt/conda/lib/python3.11/site-packages/pandas/io/parsers/readers.py:948, in read_csv(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, skipfooter, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, date_format, dayfirst, cache_dates, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, doublequote, escapechar, comment, encoding, encoding_errors, dialect, on_bad_lines, delim_whitespace, low_memory, memory_map, float_precision, storage_options, dtype_backend)
        935 kwds_defaults = _refine_defaults_read(
        936     dialect,
        937     delimiter,
       (...)
        944     dtype_backend=dtype_backend,
        945 )
        946 kwds.update(kwds_defaults)
    --> 948 return _read(filepath_or_buffer, kwds)


    File /opt/conda/lib/python3.11/site-packages/pandas/io/parsers/readers.py:611, in _read(filepath_or_buffer, kwds)
        608 _validate_names(kwds.get("names", None))
        610 # Create the parser.
    --> 611 parser = TextFileReader(filepath_or_buffer, **kwds)
        613 if chunksize or iterator:
        614     return parser


    File /opt/conda/lib/python3.11/site-packages/pandas/io/parsers/readers.py:1448, in TextFileReader.__init__(self, f, engine, **kwds)
       1445     self.options["has_index_names"] = kwds["has_index_names"]
       1447 self.handles: IOHandles | None = None
    -> 1448 self._engine = self._make_engine(f, self.engine)


    File /opt/conda/lib/python3.11/site-packages/pandas/io/parsers/readers.py:1705, in TextFileReader._make_engine(self, f, engine)
       1703     if "b" not in mode:
       1704         mode += "b"
    -> 1705 self.handles = get_handle(
       1706     f,
       1707     mode,
       1708     encoding=self.options.get("encoding", None),
       1709     compression=self.options.get("compression", None),
       1710     memory_map=self.options.get("memory_map", False),
       1711     is_text=is_text,
       1712     errors=self.options.get("encoding_errors", "strict"),
       1713     storage_options=self.options.get("storage_options", None),
       1714 )
       1715 assert self.handles is not None
       1716 f = self.handles.handle


    File /opt/conda/lib/python3.11/site-packages/pandas/io/common.py:718, in get_handle(path_or_buf, mode, encoding, compression, memory_map, is_text, errors, storage_options)
        715     codecs.lookup_error(errors)
        717 # open URLs
    --> 718 ioargs = _get_filepath_or_buffer(
        719     path_or_buf,
        720     encoding=encoding,
        721     compression=compression,
        722     mode=mode,
        723     storage_options=storage_options,
        724 )
        726 handle = ioargs.filepath_or_buffer
        727 handles: list[BaseBuffer]


    File /opt/conda/lib/python3.11/site-packages/pandas/io/common.py:372, in _get_filepath_or_buffer(filepath_or_buffer, encoding, compression, mode, storage_options)
        370 # assuming storage_options is to be interpreted as headers
        371 req_info = urllib.request.Request(filepath_or_buffer, headers=storage_options)
    --> 372 with urlopen(req_info) as req:
        373     content_encoding = req.headers.get("Content-Encoding", None)
        374     if content_encoding == "gzip":
        375         # Override compression based on Content-Encoding header


    File /opt/conda/lib/python3.11/site-packages/pandas/io/common.py:274, in urlopen(*args, **kwargs)
        268 """
        269 Lazy-import wrapper for stdlib urlopen, as that imports a big chunk of
        270 the stdlib.
        271 """
        272 import urllib.request
    --> 274 return urllib.request.urlopen(*args, **kwargs)


    File /opt/conda/lib/python3.11/urllib/request.py:216, in urlopen(url, data, timeout, cafile, capath, cadefault, context)
        214 else:
        215     opener = _opener
    --> 216 return opener.open(url, data, timeout)


    File /opt/conda/lib/python3.11/urllib/request.py:525, in OpenerDirector.open(self, fullurl, data, timeout)
        523 for processor in self.process_response.get(protocol, []):
        524     meth = getattr(processor, meth_name)
    --> 525     response = meth(req, response)
        527 return response


    File /opt/conda/lib/python3.11/urllib/request.py:634, in HTTPErrorProcessor.http_response(self, request, response)
        631 # According to RFC 2616, "2xx" code indicates that the client's
        632 # request was successfully received, understood, and accepted.
        633 if not (200 <= code < 300):
    --> 634     response = self.parent.error(
        635         'http', request, response, code, msg, hdrs)
        637 return response


    File /opt/conda/lib/python3.11/urllib/request.py:563, in OpenerDirector.error(self, proto, *args)
        561 if http_err:
        562     args = (dict, 'default', 'http_error_default') + orig_args
    --> 563     return self._call_chain(*args)


    File /opt/conda/lib/python3.11/urllib/request.py:496, in OpenerDirector._call_chain(self, chain, kind, meth_name, *args)
        494 for handler in handlers:
        495     func = getattr(handler, meth_name)
    --> 496     result = func(*args)
        497     if result is not None:
        498         return result


    File /opt/conda/lib/python3.11/urllib/request.py:643, in HTTPDefaultErrorHandler.http_error_default(self, req, fp, code, msg, hdrs)
        642 def http_error_default(self, req, fp, code, msg, hdrs):
    --> 643     raise HTTPError(req.full_url, code, msg, hdrs, fp)


    HTTPError: HTTP Error 404: Not Found



```python
# Once again, ChatGPT was much more helpful in resolving this issue, pointing out the problem and providing the exact
# code needed to fix it, while Google was unable to provide an immediate solution
```


```python
import pandas as pd
url = "https://raw.githubusercontent.com/mwaskom/seaborn-data/master/titanic.csv"
df = pd.read_csv(url)
print(df)
```

         survived  pclass     sex   age  sibsp  parch     fare embarked   class  \
    0           0       3    male  22.0      1      0   7.2500        S   Third   
    1           1       1  female  38.0      1      0  71.2833        C   First   
    2           1       3  female  26.0      0      0   7.9250        S   Third   
    3           1       1  female  35.0      1      0  53.1000        S   First   
    4           0       3    male  35.0      0      0   8.0500        S   Third   
    ..        ...     ...     ...   ...    ...    ...      ...      ...     ...   
    886         0       2    male  27.0      0      0  13.0000        S  Second   
    887         1       1  female  19.0      0      0  30.0000        S   First   
    888         0       3  female   NaN      1      2  23.4500        S   Third   
    889         1       1    male  26.0      0      0  30.0000        C   First   
    890         0       3    male  32.0      0      0   7.7500        Q   Third   
    
           who  adult_male deck  embark_town alive  alone  
    0      man        True  NaN  Southampton    no  False  
    1    woman       False    C    Cherbourg   yes  False  
    2    woman       False  NaN  Southampton   yes   True  
    3    woman       False    C  Southampton   yes  False  
    4      man        True  NaN  Southampton    no   True  
    ..     ...         ...  ...          ...   ...    ...  
    886    man        True  NaN  Southampton    no   True  
    887  woman       False    B  Southampton   yes   True  
    888  woman       False  NaN  Southampton    no  False  
    889    man        True    C    Cherbourg   yes   True  
    890    man        True  NaN   Queenstown    no   True  
    
    [891 rows x 15 columns]



```python
DF.groupby("survived")["pclass"].describe
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Cell In[6], line 1
    ----> 1 DF.groupby("survived")["pclass"].describe


    NameError: name 'DF' is not defined



```python
pd.read_csv(url
```


      Cell In[7], line 1
        pd.read_csv(url
                       ^
    SyntaxError: incomplete input




```python
df.groupby("survived")["pclass"].describle()
```


    ---------------------------------------------------------------------------

    AttributeError                            Traceback (most recent call last)

    Cell In[9], line 1
    ----> 1 df.groupby("survived")["pclass"].describle()


    File /opt/conda/lib/python3.11/site-packages/pandas/core/groupby/groupby.py:1312, in GroupBy.__getattr__(self, attr)
       1309 if attr in self.obj:
       1310     return self[attr]
    -> 1312 raise AttributeError(
       1313     f"'{type(self).__name__}' object has no attribute '{attr}'"
       1314 )


    AttributeError: 'SeriesGroupBy' object has no attribute 'describle'



```python
df.groupby("Sex")["age"].describe()
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    Cell In[12], line 1
    ----> 1 df.groupby("Sex")["age"].describe()


    File /opt/conda/lib/python3.11/site-packages/pandas/core/frame.py:8869, in DataFrame.groupby(self, by, axis, level, as_index, sort, group_keys, observed, dropna)
       8866 if level is None and by is None:
       8867     raise TypeError("You have to supply one of 'by' and 'level'")
    -> 8869 return DataFrameGroupBy(
       8870     obj=self,
       8871     keys=by,
       8872     axis=axis,
       8873     level=level,
       8874     as_index=as_index,
       8875     sort=sort,
       8876     group_keys=group_keys,
       8877     observed=observed,
       8878     dropna=dropna,
       8879 )


    File /opt/conda/lib/python3.11/site-packages/pandas/core/groupby/groupby.py:1278, in GroupBy.__init__(self, obj, keys, axis, level, grouper, exclusions, selection, as_index, sort, group_keys, observed, dropna)
       1275 self.dropna = dropna
       1277 if grouper is None:
    -> 1278     grouper, exclusions, obj = get_grouper(
       1279         obj,
       1280         keys,
       1281         axis=axis,
       1282         level=level,
       1283         sort=sort,
       1284         observed=False if observed is lib.no_default else observed,
       1285         dropna=self.dropna,
       1286     )
       1288 if observed is lib.no_default:
       1289     if any(ping._passed_categorical for ping in grouper.groupings):


    File /opt/conda/lib/python3.11/site-packages/pandas/core/groupby/grouper.py:1009, in get_grouper(obj, key, axis, level, sort, observed, validate, dropna)
       1007         in_axis, level, gpr = False, gpr, None
       1008     else:
    -> 1009         raise KeyError(gpr)
       1010 elif isinstance(gpr, Grouper) and gpr.key is not None:
       1011     # Add key to exclusions
       1012     exclusions.add(gpr.key)


    KeyError: 'Sex'



```python
df.groupby("sex")[age].describe()
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    Cell In[13], line 1
    ----> 1 df.groupby("sex")[age].describe()


    NameError: name 'age' is not defined



```python
# For all of the situations of question 8 subquestion 3, ChatGPT was a much more helpful and easy tool to use in 
# comparison to Google Search, helping me to troubleshoot and provided me with necessary solutions.
```


```python
https://chatgpt.com/share/d555b589-969e-47d0-99d0-f1234fe134e2
```
