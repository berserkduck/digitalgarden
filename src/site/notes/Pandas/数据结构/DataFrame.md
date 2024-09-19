---
{"dg-publish":true,"permalink":"/Pandas/数据结构/DataFrame/"}
---

# DataFrame对象
DataFrame对象（简称DataFrame），可以理解成一张二维表，包含一组有序的列（字段），每列可以存储不同类型的数据
DataFrame既有行索引又有列索引，类似于Excel中的行号和列标
# 构造方法
```python
pandas.DataFrame(
	data=None, 
	index=None, 
	columns=None, 
	dtype=None, 
	copy=False
)
```
- `data`：DataFrame 的数据部分，可以是字典、二维数组、Series、DataFrame 或其他可转换为 DataFrame 的对象。如果不提供此参数，则创建一个空的 DataFrame。
- `index`：DataFrame 的行索引，用于标识每行数据。可以是列表、数组、索引对象等。如果不提供此参数，则创建一个默认的整数索引。
- `columns`：DataFrame 的列索引，用于标识每列数据。可以是列表、数组、索引对象等。如果不提供此参数，则创建一个默认的整数索引。
- `dtype`：指定 DataFrame 的数据类型。可以是 NumPy 的数据类型，例如 `np.int64`、`np.float64` 等。如果不提供此参数，则根据数据自动推断数据类型。
- `copy`：是否复制数据。默认为 False，表示不复制数据。如果设置为 True，则复制输入的数据。