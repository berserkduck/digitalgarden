---
{"dg-publish":true,"permalink":"/Pandas/文件操作/Excel文件/"}
---

# 写入Excel
```python
import pandas as pd

data = [  
    [1, '张三', '1999-3-10', 25],  
    [2, '李四', '2002-3-10', 15],  
    [3, '王五', '1990-3-10', 33],  
    [4, '赵六', '1983-3-10', 40]  
]  
  
df = pd.DataFrame(data, columns=['id', 'name', 'birthday', 'age'])  
df
```

默认读取，会在My_output目录生成一个student.xls文件
```python
df.to_excel('../My_output/student.xls')
```

路径使用点点，表示上级目录
```
.
├── output_folder
└── code_folder
    └── code
```

路径使用点，表示同级目录
```
.
├── output_folder
└── code
```

### 常用的参数
去掉索引
```python
df.to_excel('../My_output/student.xls', index=False) # 去掉索引
```
去掉索引和标题
```Python
df.to_excel('../output/student.xls', index=False, header=False)
```
指定sheet名
```Python
df.to_excel('../output/student.xls', index=False, header=False, sheet_name='学生信息')
```
# 读取Excel
```python
import pandas as pd

df = pd.read_excel('data.xlsx')
df
```
## 常用参数
#todo