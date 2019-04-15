# re  正则表达式
[正则表达式操作](https://docs.python.org/zh-cn/3/library/re.html?highlight=re#module-re)
## 概述
用来描述或者匹配一系列符合某种规则得字符串的表达式  
（输入用户名密码，长度不够，特殊符号，怎样知道输入的格式对不对）
## 正则表达式
### 元字符
```
# \w 字符
# res = re.findall(r"\w","123abcdef_$^<>")        # \w只匹配一个字符,命名的时候可以命名什么
# print(res)
# \W 非字符
# res = re.findall(r"\W","123abcdef_$^<>")
# print(res)
# \d 数字
# res = re.findall(r"\d","123abcdef_$^<>")
# print(res)
# \D 非数字
# res = re.findall(r"\D","123abcdef_$^<>")
# print(res)
# \b 单词边界(单词边界就是空)
# res = re.findall(r"\bi","this is div")
# print(res)
# \B 非单词边界
# res = re.findall(r"\Bi","this is div")
# # print(res)
# \s 空
# res = re.findall(r"\s","this is div")
# print(res)
# \S 非空
# res = re.findall(r"\S","this is div")
# print(res)
# . 除了\n 以外的所有字符
# res = re.findall(r".","this is div")
# print(res)

```
### 原子表
原子表   也是匹配一位字符,可以连一起找  
  []    类似一个列表
  ```
  # [abc]
# [a-z]
# [A-Z]
# [a-zA-Z1-9]
# [^...]  取反
# res = re.findall(r"[hs]","this is div")     # 匹配h和s
# res = re.findall(r"[a-z]","this is DIV")        # 匹配小写字母
# res = re.findall(r"[^A-Z]","this is DIV")        # 取反
# print(res)
```
### 数量
```
*   0个或多个字符
+   1个或多个
？  0个或1个
{n}    n个
{n,}  n个或多个
{n,m}  n个到m个
res = re.findall(r"\w*","this is div")
res = re.findall(r"\w+","this is div")
res = re.findall(r"\w?","this is div")
res = re.findall(r"an?","this is a an div")     # 后边的n可有可无
res = re.findall(r"</?div>?","<div>this is div</div>")      # / 可有可无
res = re.findall(r"\w{2}","abcdefg")
res = re.findall(r"\w{2,3}","this is div")      # 贪婪特点：尽可能多
res = re.findall(r"\w{2,}","this is div")       # 贪婪： 选择全部
print(res)
```
### 其他
^  以什么开始  
$   以什么结束  
a|b  a或b  
()   表示一个组  
```
  () 组
  (?P=name)  命名组、定义组
  正则表达式中调用   (?P=name)    \1  \2..
  正则对象中  res.group(n)   res.groupdict()

res4 = re.search(r'<?P<tag>\w+>(?P<con>.*)</(?P=tag)>','<div>this is div</div>')
res4 = re.search(r'<?P<tag>\w+>(?P<con>.*)</(\1)>','<div>this is div</div>')
print(res4)
```
### re 模块
* 匹配模式
re.I  忽略大小写   
re.L  表示特殊字符集 \w , \W,  \b ,\B, \s ,\S 依赖于当前环境  
re.M  多行模式  
re.S  使特殊字符匹配任何字符，包括换行，如果没有此标志，将匹配任何内容除换行符  
re.X  此标志允许编写正则表达式，看起来更好。在模式中的空白将被忽略，除非当在字符类或者前面非转义反斜杠和当一条线包含一个# ，既不在字符类中或由非转义反斜杠，从最左侧的所有字符之前，这种# 通过行末尾将被忽略。
```
## 匹配模式
# rege = re.compile('[a-z]',re.I)        # re.I忽略大小写
# res = rege.findall("absdhoashODISAHNO")
# print(res)

# rege = re.compile("""[a-z] # 字母""",re.X)
# res = rege.findall("""
# absdhoashODISAHNO
# hfadshfi
# """)
# print(res)
```
* [re常用函数](re常用函数.md)