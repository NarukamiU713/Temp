# 代码疑难 (1)
**Contents**
- [一、Python二维数组的构建](#一、Python二维数组的构建)
- [二、Split分词语法](#二、Split分词语法)
- [三、](#三、)
### 一、Python二维数组的构建

#### 1.手动构建
```python
	matrix = [[0, 0, 0], [0, 0, 0], [0, 0, 0]] 
	# 3*3 initialization
```
#### 2.列表式构建
```python
	matrix = [[0] * 3 for _ in range(3)]  
	# Aware that the first 3 is the Cols, then the Rows
```
#### 3.对比C
```c
	int matrix[3][3] = {0}
```
#### 4.跨文件构建数组
```python
	with open file('data.txt') as f: # Assign the data file to f
		matrix = [list(map(int, line.split())) for line in f]
```
**We can take it into split parts.**

1.`for line in f` is to iterate the lines in data file.

2.`line.split()` is to take datas apart by spaces.
```python
	line = "1 2 3"
	line.split()      # → return ['1', '2', '3']
```
3.`map(datatype, x)` is to transform every element in x into one datatype.
```python
	str_list = ['1', '2', '3']
	map(int, str_list)  # → equals to [1, 2, 3]
	# → return some kind of iterator
```
4.`list()` is to transform the iterator into one real list.
```python
	list(...)      # → return [1, 2, 3]
```
### 二、Split分词语法
用于处理复杂数据，滤掉无用的信息。
#### 1.空白符分割
```python
	text = "apple banana  cherry   date"
	print(text.split())
	# → ['apple', 'banana', 'cherry', 'date']
```
#### 2.特殊符分割
**Split by the signs in the parentheses.**
```python
	csv = "a,b,c,d"
	print(csv.split(','))  # → ['a', 'b', 'c', 'd']
```
#### 3.限制次数分割
```python
	csv = "a,b,c,d"
	print(csv.split(',', 2))  # → ['a', 'b', 'c,d']
```
#### 4.分割并除空字符串

```python
	text = "data;;;entries;;"
	print(text.split(';'))  
	# → ['data', '', '', 'entries', '', '']
```
Using ``s for s in text.split('...') if s`` to clear the empty strings.
```python
	print([s for s in text.split(';') if s])  
	# → ['data', 'entries']
```
`*Notice: Do not forget to add this '[...]'!`
#### 5.多符号处理
```python
	import re
	text = "apple,banana;cherry|date"
	print(re.split(r'[,;|]', text))
	# → ['apple', 'banana', 'cherry', 'date']
```

### 三、
