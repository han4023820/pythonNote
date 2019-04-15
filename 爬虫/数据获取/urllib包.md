# urllib包  （包里有丰富的API）
* [URL 处理模块](https://docs.python.org/zh-cn/3/library/urllib.html#module-urllib)
## 概述
uillib是一个收集了多个使用URL的模块的软件包
## 组件
request：打开和阅读url地址的包  
* [urllib.request --- 用于打开 URL 的可扩展库](https://docs.python.org/zh-cn/3/library/urllib.request.html?highlight=urllib%20request#module-urllib.request)  

urllib.request
    urlopen  
error：包含 urllib.request 抛出的异常
    urllib.error  
parse：用于处理 URL[官网详细内容](https://docs.python.org/zh-cn/3/library/urllib.parse.html?highlight=urllib%20parse#module-urllib.parse)
urllib.parse
* 编码转换
	* parse.urlencode({}）
	* quote("太原"）把汉字转换为编码
* urlparse(url)
	* 解析url各个部分
* robotparser：用于解析 robots.txt 文件
urllib.robotparser
## 响应类型为json
[JSON 编码和解码器](https://docs.python.org/zh-cn/3/library/json.html?highlight=json#module-json)  

	json.loads(str)      将 str 转换为 dict
	json.dumps(dict)     将 dict 转换为 str