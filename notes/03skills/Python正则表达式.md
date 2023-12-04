# Python正则表达式

> 情况：在一个EXCEL文件中，记录了众多公司的账目，单位有万元和亿元，彼此混杂。现想把单位统一为万元，且不显示出来

法一：利用EXCEL的公式

```sql
= IF(VALUE(MID(B2,1,5)) < 1000, MID(B2,1,5)*10000, MID(B2, 1, 5))
```

​		此法比较受数据特征局限。如上述公式，只能应对千万到百亿之间的金额而且要位数固定

法二：用正则表达式

当然，C++11的\<regex\>库也可以，但是这么一个小东西python足够了

## [python正则表达式](https://www.runoob.com/python/python-reg-expressions.html)

- `re.search(pattern, string) -> Optional[Match[AnyStr]]`查找
- `re.findall(pattern, string) -> list[anystr]`  查找全部
- `re.sub(pattern, repl, string) -> the string` 替换全部
- `re.split(pattern, string) -> list[anystr]` 以pattern为界限分割

统统可加一个`flags`选项

可以对正则表达式进行分组：

 1.  `r"([a-z]+)([1-9]+)"`，括号分别编号为`group(1)`, `group(2)`

 2.  `r"(?P<name1>[a-z]+)([1-9]+)"`，在编号的基础上，用`(?P<name1>)`又给分组指定了名字name1

     

下面是一个例子

```python
import re

def convert_yi(matched):
    yi = float(matched.group('yi'))
    return str(format(yi * 10000, '.0f'))

def convert_wan(matched):
    wan = float(matched.group('wan'))
    return str(format(wan, '.0f'))

infile = open("D:\\codes\\test\\abc.csv", "r", encoding='UTF-8')
outfile = open("D:\\codes\\test\\result.csv", "a", encoding='UTF-8')

for line in infile.readlines():
    temp = re.sub('(?P<yi>[-\.0-9]+)(亿)', convert_yi, line)
    temp2 = re.sub('(?P<wan>[-\.0-9]+)(万)', convert_wan, temp)
    outfile.write(temp2)

infile.close()
outfile.close()
```

