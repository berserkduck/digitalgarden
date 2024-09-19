---
{"dg-publish":true,"permalink":"/Pandas/数据结构/Series/"}
---


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/excalidraw/pandas/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Pandas数据结构

</div>



==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data
## Text Elements
DataFrame 
行索引 
列索引或字段 
Series 


</div></div>

# Series对象
Series对象（简称Series）可以理解成“一列数据”，是一种类似于一维数组的对象，由两部分组成：
1. index：行索引，默认为0~N-1
2. values：值，numpy.ndarray类型（[[Pandas/数据结构/n维数组\|n维数组]]）
# Series的特点
- **一维**：类似Python中的列表
- **索引**：每个Series都有一个索引，可以是整数、字符串、日期等类型。默认从0开始
- **数据类型**：可容纳不同类型的元素，包括整数、浮点数、字符串、Python 对象等
- **大小不变**；Series创建后是不变的
- **操作**：数学运算、统计分析、字符串处理
- **缺失数据**：Series可以包含缺失数据，Pandas 使用NaN（Not a Number）来表示缺失或无值
# 构造方法
使用Pandas要导入Pandas包，pd是标准别名
```python
import pandas as pd
```

```python
pandas.Series(
	data=None, 
	index=None, 
	dtype=None, 
	name=None, 
	copy=False, 
	fastpath=False
)
```

- `data`：Series 的数据部分，可以是列表、数组、字典、标量值等。如果不提供此参数，则创建一个空的 Series。
- `index`：Series 的索引部分，用于对数据进行标记。可以是列表、数组、索引对象等。如果不提供此参数，则创建一个默认的整数索引。
- `dtype`：指定 Series 的数据类型。可以是 NumPy 的数据类型，例如 `np.int64`、`np.float64` 等。如果不提供此参数，则根据数据自动推断数据类型。
- `name`：Series 的名称，用于标识 Series 对象。如果提供了此参数，则创建的 Series 对象将具有指定的名称。
- `copy`：是否复制数据。默认为 False，表示不复制数据。如果设置为 True，则复制输入的数据。
- `fastpath`：是否启用快速路径。默认为 False。启用快速路径可能会在某些情况下提高性能。
# 创建Series
## 使用列表创建Series
```python
import pandas as pd

s1 = pd.Series([1,2,3])
```
### s1和print(s1)
```python
s1

>>>
+-+---------+
| |<unnamed>|
+-+---------+
|0|1        |
|1|2        |
|2|3        |
+-+---------+
```

```python
print(s1)

>>>
0    1
1    2
2    3
dtype: int64
```
> dtype：int64是该Series对象中**值的数据类型**
> 如果列表里保存有不同类型的数据（字符串和整数），dtype类型是object

```python
print(type(s1))

>>>
<class 'pandas.core.series.Series'>
```
### 指定索引与列名
```python
s = pd.Series([1,2,3], index=['a', 'b', 'c'], name='x')  
s

>>>
+-+-+
| |x|
+-+-+
|a|1|
|b|2|
|c|3|
+-+-+
```

## 使用NumPy数组创建Series
```python
import pandas as pd  
import numpy as np  
  
s = pd.Series(np.array([1, 2, 3, 4]))  
s

>>>
+-+---------+
| |<unnamed>|
+-+---------+
|0|1        |
|1|2        |
|2|3        |
|3|4        |
+-+---------+
```
## 使用字典创建Series
字典的键会被指定为Series的索引
```python
s = pd.Series({'a': 1, 'b': 2, 'c': 3, 'd': 4})
s

>>>
+-+---------+
| |<unnamed>|
+-+---------+
|a|1        |
|b|2        |
|c|3        |
|d|4        |
+-+---------+
```

获取指定索引的数据
```python
s = pd.Series({'a': 1, 'b': 2, 'c': 3, 'd': 4}, index=['a', 'b', 'c'])  
s

>>>
+-+---------+
| |<unnamed>|
+-+---------+
|a|1        |
|b|2        |
|c|3        |
+-+---------+
```

如果索引不存在，含显示空，这个Series的类型会变成float64
```python
s = pd.Series({'a': 1, 'b': 2, 'c': 3, 'd': 4}, index=['x', 'b', 'c'])  
s

>>>
+-+---------+
| |<unnamed>|
+-+---------+
|x|NaN      |
|b|2.0      |
|c|3.0      |
+-+---------+
```
