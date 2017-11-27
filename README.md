# Question_Records
Record the questions encountered in data clearning

- 1.在筛选同时不满足两个条件的数据时，数据库中可以使用sql中的minus语句完成
```sql
select * from
(
select * from a 
minus
select * from a.c1<>1 and a.c2<>2
)
```
但是在Python的DataFrame中无法完成，DataFrame中的条件筛选是顺序执行，例如
```python
import pandas as pd
import numpy as np

d1=pd.DataFrame(np.arange(1,22).reshape(7,-1)
d1[1]=[1,1,1,2,2,2,2]
d1[2]=[3,3,3,3,3,4,4]

d1[(d1[1]!=1)&(d1[2]!=3)]

    0  1  2
5  16  2  4
6  19  2  4
```
而我想查出的结果为
```
    0  1  2
3  10  2  3
4  13  2  3
5  16  2  4
6  19  2  4
```
