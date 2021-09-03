# Python
#伪装浏览器的爬虫
from urllib import request
import re
import random 
url=r"http://www.baidu.com/"
agent1="Mozilla/5.0 (Windows NT 10.0; WOW64)\
AppleWebKit/537.36 (KHTML, like Gecko) Chrome/72.0.3626.81 \
Safari/537.36 SE 2.X MetaSr 1.0"
agent2="Mozilla/5.0 (iPhone; U; CPU iPhone OS 4_3_3 like Mac OS X; en-us)\
AppleWebKit/533.17.9 (KHTML, like Gecko) Version/5.0.2 Mobile/8J2 Safari/6533.18.5"
agent3="Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; Trident/5.0"
agent4="Mozilla/5.0 (Windows NT 6.1; rv:2.0.1) Gecko/20100101 Firefox/4.0.1"
agent5="Opera/9.80 (Windows NT 6.1; U; en) Presto/2.8.131 Version/11.11"
list1=[agent1,agent2,agent3,agent4,agent5]
agent=random.choice(list1)
print(agent)
#构造请求头信息
header={"User-Agent":"agent"}
#创建自定义请求对象   
#反爬虫机制1：判断用户是否是浏览器访问
#可以通过伪装浏览器进行访问
req=request.Request(url,headers=header)
#发送请求.获取响应信息
reponse=request.urlopen(req).read().decode() #解码---（编码encode()）
pat=r"<title>(.*?)</title>"
data=re.findall(pat,reponse)
print(data[0])
