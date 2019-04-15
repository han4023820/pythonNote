# re常用函数
## re.match(pattern,string,flags=0)
* pattern  正则表达式  
  steing  要匹配的字符串  
  flag  模式
* 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，
* 成功返回正则对象
	* group(num=0)
	* groups()
## re.search(pattern,string,flags=0)
* pattern  正则表达式
  steing  要匹配的字符串
  flag  模式
* re.search() 扫描整个字符串并返回第一个成功的匹配
* 成功返回正则对象
	* group(num=0)
	* groups()
## re.sub(pattern,repl,string,count=0,flags=0)
pattern  正则中的模式字符串  
repl  替换的字符串也可为一个函数  
string  要被查找替换的原始字符串  
count  模式匹配后替换的最大次数，默认0，表示替换所有的匹配  
```
## sub  替换函数
# res = re.sub("山西","陕西","山西优逸客","陕西",1)
# def fn(a):
#     res = str(int(a.group())*2)
#     return res
#
# res = re.sub("\d+",fn,"山西优逸客 就业人数1000 高薪就业900")
# print(res)
```
## re.compile(pattern[,flags])
返回一个迭代器。可以循环的、一次性输出
## re.split(pattern,string[,maxsplit=0,flags=0])
pattern  匹配的正则表达式  
string  要匹配的字符串  
maxsplit  分割次数  
flags  标志位  
```
## split 拆分函数
# rege = re.compile('[;,.]')     # 正则表达式,变成原子表
# res5 = rege.split('a;b,c.d')
# res5 = re.split('[;,.]','a;b,c.d')
# print(res5)
```