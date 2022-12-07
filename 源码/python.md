

# 实例

## 猜数字

### 第一版

```python
print("来猜数字吧\n")

import random
a = random.randint(1,1001) # 随机生成1~256的数字

while 1:
    temp = input("输入你猜的数字 区间为1~1000:")
    guess = int(temp)
    if a == guess:
        break
    if a < guess:
        print("\n 大了\n")
    else:
        print("\n 小了\n")
print("猜对了哦^-^游戏结束~~")
```

### 第二版 esaygui图形界面版

```python
import easygui as g
import random as r

g.msgbox("来猜数字吧","猜数字")
while 1:
    nummin,nummax = map(int,g.multenterbox(msg="请输入你想要猜的数的范围(整数)"
                        ,title="选定范围",fields=["最小值","最大值"]))
    
    if nummin < nummax:
        break
    else:
        pfint("输入有误 请按正确格式输入")
        
# 确定随机数的范围
i = 0
# 记录一共猜了多少次
num = r.randint(nummin,nummax+1) 
#进行随机
while 1:
    i +=1
    temp =g.integerbox(msg="请输入你要猜的数字\n范围为%d - %d"%(nummin,nummax)
                      ,title="猜数字",lowerbound=nummin,upperbound=nummax)
    if temp > num:
        nummax = temp
        continue
    if temp < num:
        nummin = temp
        continue
    if temp == num:
        g.msgbox("恭喜你回答正确一共用了%d次机会"%(i),"猜数字")
        break
```

## 求范围内有多少个素数

```python
print("请输入你要求素数得范围 中间用空格隔开")
a,b = map(int,input().split())

print("得出的素数如下\n")

if a <= 2 <= b:
    sum = 1
    print(2)
else:
    sum = 0
for i in range(a,b):
    for j in range(2,i):
        if i%j == 0:
            break
        if j == i-1:
            print(i)
            sum += 1
print("一共有%d个素数" % sum)
```

## 求数字阶层

```python     
def jc(n):
    if n == 1:
        return 1
    if n > 1:
        return n * jc(n-1)

num = int(input("此程序为求阶层\n请输入一个正整数:"))
he = jc(num)
print(" %d 的阶层为 %d "% (num,he))
```

## 五角星数

​	五角星数是指某个五位数，其每一位的五次方加起来还等于这个数，
​	例如：	对于五位数54748，5^5=3125 4^5=1024 7^5=16807 8^5=32768 加起来的和为51748
​	那么总共有多少个五角星数？他们分别为？

```python
i = 10000
sum = 0
while( i < 100000 ):
    if i == (pow(i%10,5) + pow((i%100-i%10)/10,5)+
             pow((i%1000-i%100)/100,5)+pow((i%10000-i%1000)/1000,5)+
             pow(int(i/10000),5)):
        print(i)
        sum += 1
    i += 1
        
print("一共有",和,"个五角星数")
```

## 兔子问题（斐波那契数列）

​	假设一对兔子的成熟期是一个月，即一个月可长成成兔，
​	那么，如果每对成兔每个月都生一对小兔，一对新生的小兔从第二个月起就开始生兔子，
​	试问从一对兔子开始繁殖，以后每个月会有多少对兔子？         

```python
month = int ( input("请输入你要查看的月份数："))
ynq = 1
csq = 0
for i in range(month):
    if i < month:
        t = csq             #这个月成熟的数量
        csq += ynq           #下个月成熟的数量 这个月一共的兔子数量
        ynq = t             #这个月生的兔子数
print("到了第%d月一共有 %d 只兔子"%(month,csq))
```

## 龟吃鱼

游戏编程：按以下要求定义一个乌龟类和鱼类并尝试编写游戏。
a.假设游戏场景为范围（x,y）为0<=x<=10，0<=y<=10
b.游戏生成1只乌龟和10条鱼
c.它们的移动方向均随机
d.乌龟的最大移动能力是2（Ta可以随机选择1还是2移动），鱼儿的最大移动能力是1
e.当移动到场景边缘，自动向反方向移动
f.乌龟初始化体力为100（上限）
g.乌龟每移动一次，体力消耗1
h.当乌龟和鱼坐标重叠，乌龟吃掉鱼，乌龟体力增加20
i.鱼暂不计算体力
j.当乌龟体力值为0（挂掉）或者鱼儿的数量为0游戏结束

```python
import random as r

hp = 100 #乌龟初始体力为100
num = 0  #鱼儿被吃掉的数量

  
class Trutle:

    def __init__(self):
        self.x = r.randint(0,10)    #初始位置
        self.y = r.randint(0,10)

    def mobile(self):
        new_x = self.x + r.choice([1,-1,2,-2])  #龟开始移动
        new_y = self.y + r.choice([1,-1,2,-2])

        if new_x < 0:
            self.x = 0 - (new_x - 0)
        elif new_x > 10:
            self.x = 10 - (new_x - 10)
        else:
            self.x = new_x

        if new_y < 0:
            self.y = 0 - (new_y - 0 )
        elif new_y > 10:
            self.y = 10 - (new_y - 10)
        else:
            self.y = new_y

        return (self.x, self.y)
            
class Fish:
    def __init__(self):
        self.x = r.randint(0,10)    #鱼的初始位置
        self.y = r.randint(0,10)
    
    def mobile(self):
        new_x = self.x + r.choice([1,-1])  
        new_y = self.y + r.choice([1,-1])

        if new_x < 0:
            self.x = 0 - (new_x - 0 )
        elif new_x > 10:
            self.x = 10 - (new_x - 10)
        else:
            self.x = new_x

        if new_y < 0:
            self.y = 0 - (new_y - 0 )
        elif new_y > 10:
            self.y = 10 - (new_y - 10)
        else:
            self.y = new_y
            
        return (self.x, self.y)
        
            
trutle = Trutle()
fish = []
for i in range(10):             #把10条鱼的数据储存在表中
    new_fish = Fish()
    fish.append(new_fish)

while 1:
    T = trutle.mobile()
    for i in fish:
        if i.mobile() == T:
            
            hp += 20            #吃鱼恢复体力 上限100
            if (hp > 100):
                hp = 100
                
            fish.remove(i)
            print("有一条鱼被吃了")
            num += 1
    hp -= 1
    if (hp == 0):
        print("乌龟体力不足游戏结束 一共吃了%d条鱼"%(num))
        break
        
    if num == 10:
        print("10条鱼全部吃完了，游戏结束")
        break
```

## 计时器

* 定制一个计时器的类。

* start和stop方法代表启动计时和停止计时。

* 假设计时器对象t1，print(t1)和直接调用t1均显示结果。

* 当计时器未启动或已经停止计时，调用stop方法会给予温馨的提示。

* 两个计时器对象可以相加：t1+t2。

* 只能使用提供的有限资源完成。

需要用到下面这些资源：

* 使用time模块的localtime方法获取时间
* time.localtime返回struct_time的时间格式。
* _ _ str_ _ ()和_ _ repr_ _()魔法方法。

其中，_ _ str _ _ ()和 _ _repr _ _()魔法方法的用法很简单：

```python
>>>	class A:
	def __str__(self):
		return"你好世界"
    
>>>	a = A()        
>>> print(a)
你好世界
>>>	a 
#<__main_.A object at 0x03260F30>
>> class B:
	def __repr__(self)
		return "你好世界！"
    
>>>	b = B()
>>>	b
你好世界！
```

### 我的版本

```python
import time as t

class MyTimer:
    def __init__(self):
        self.count = 0  # 计算是否开始计时
   
	# 计时开始
    def start(self):	
        self.start = t.localtime()
        self.count = 1
        print("计时开始…")
	
    # 计时结束
    def stop(self):
        if self.count == 0:
            print("提示:请先调用 start() 开始计时")
        else:
            self.stop = t.localtime()
            self.time = self.stop[4]*60+self.stop[5]-self.start[4]*60-self.start[5]
            self.count = 2
            print("计时结束！")

    #返回内容
    def __repr__(self):
        if self.count == 0:
            return '未开始计时！'
        if self.count == 1:
            return '提示：请先调用stop()结束计时'
        if self.count == 2:
            return '总共运行了%d秒' % (self.time)

    #重写add方法
    def __add__ (self,other):
        time = self.time + other.time
        a = "总共运行了"
        b = "秒"
        a += str(time)+b
        return a
```

### 小甲鱼版本

```python
import time as t

class MyTimer:
    def __init__(self):
        self.prompt = "未开始计时！"
        self.lasted = []
        self.start = 0
        self.stop = 0

    def __init__(self):
        self.unit = ['年', '月', '天', '小时', '分钟', '秒']
        self.prompt = "未开始计时！"
        self.lasted = []
        self.begin = 0
        self.end = 0

    # 开始计时
    def start(self):
        self.begin = t.localtime()
        self.prompt = "提示：请先调用 stop() 停止计时！"
        print("计时开始...")

    # 停止计时
    def stop(self):
        if not self.begin:
            print("提示：请先调用 start() 开始计时！")
        else:
            self.end = t.localtime()
            self._calc()
            print("计时结束！")

    # 计算运行时间
    def _calc(self):
        self.lasted = []
        self.prompt = "总共运行了"
        for index in range(6):
            self.lasted.append(self.end[index] - self.begin[index])
            if self.lasted[index]:
                self.prompt += (str(self.lasted[index]) + self.unit[index])
        # 为下一轮计算初始化变量
        self.begin = 0
        self.end = 0

    # 重写add方法
    def __add__(self, other):
        prompt = "总共运行了"
        result = []
        for index in range(6):
            result.append(self.lasted[index] + other.lasted[index])
            if result[index]:
                prompt += (str(result[index]) + self.unit[index])
        return prompt

    def __str__(self):
        return self.prompt
    
    __repr__ = __str__
```

## 反转整数

```python
n = 0
s = 1
if x<0:
x = x*-1
s = -1

while x != 0:
	n = n*10 + (x%10)
	x = int(x/10)

        n = s*n
```

```python
x = input("输入你要反转整数")
return int(str(x)[::-1]) if x > 0 else int((str(-x)+'-')[::-1])
```

## 求质数

埃拉托斯特尼筛法

```python
def eratosthenes(n):
    IsPrime = [True] * (n + 1)
    for i in range(2, int(n ** 0.5) + 1):
        if IsPrime[i]:
            for j in range(i * i, n + 1, i):
                IsPrime[j] = False
    return [x for x in range(2, n + 1) if IsPrime[x]]
if __name__ == "__main__":
    print(eratosthenes(120))
```



# 一些脚本

## 颠倒字符串

```python
a=input("")
b=[]
for i in a:
    b.insert(0,i)
print("".join(b))
```

## 键盘流量

```python
normalKeys = {"04":"a", "05":"b", "06":"c", "07":"d", "08":"e", "09":"f", "0a":"g", "0b":"h", "0c":"i", "0d":"j", "0e":"k", "0f":"l", "10":"m", "11":"n", "12":"o", "13":"p", "14":"q", "15":"r", "16":"s", "17":"t", "18":"u", "19":"v", "1a":"w", "1b":"x", "1c":"y", "1d":"z","1e":"1", "1f":"2", "20":"3", "21":"4", "22":"5", "23":"6","24":"7","25":"8","26":"9","27":"0","28":"<RET>","29":"<ESC>","2a":"<DEL>", "2b":"\t","2c":"<SPACE>","2d":"-","2e":"=","2f":"[","30":"]","31":"\\","32":"<NON>","33":";","34":"'","35":"<GA>","36":",","37":".","38":"/","39":"<CAP>","3a":"<F1>","3b":"<F2>", "3c":"<F3>","3d":"<F4>","3e":"<F5>","3f":"<F6>","40":"<F7>","41":"<F8>","42":"<F9>","43":"<F10>","44":"<F11>","45":"<F12>"}

shiftKeys = {"04":"A", "05":"B", "06":"C", "07":"D", "08":"E", "09":"F", "0a":"G", "0b":"H", "0c":"I", "0d":"J", "0e":"K", "0f":"L", "10":"M", "11":"N", "12":"O", "13":"P", "14":"Q", "15":"R", "16":"S", "17":"T", "18":"U", "19":"V", "1a":"W", "1b":"X", "1c":"Y", "1d":"Z","1e":"!", "1f":"@", "20":"#", "21":"$", "22":"%", "23":"^","24":"&","25":"*","26":"(","27":")","28":"<RET>","29":"<ESC>","2a":"<DEL>", "2b":"\t","2c":"<SPACE>","2d":"_","2e":"+","2f":"{","30":"}","31":"|","32":"<NON>","33":"\"","34":":","35":"<GA>","36":"<","37":">","38":"?","39":"<CAP>","3a":"<F1>","3b":"<F2>", "3c":"<F3>","3d":"<F4>","3e":"<F5>","3f":"<F6>","40":"<F7>","41":"<F8>","42":"<F9>","43":"<F10>","44":"<F11>","45":"<F12>"}


nums = []
keys = open('1.txt')
for line in keys:
    if len(line)!=17: #首先过滤掉鼠标等其他设备的USB流量
         continue
    nums.append(line[0:2]+line[4:6]) #取一、三字节
keys.close()
output = ""
for n in nums:
    if n[2:4] == "00" :
        continue

    if n[2:4] in normalKeys:
        if n[0:2]=="02": #表示按下了shift
            output += shiftKeys [n[2:4]]
        else :
            output += normalKeys [n[2:4]]
    else:
        output += '[unknown]'
print('output :n' + output)
```

鼠标流量

```python
#sniffer.py
nums = []
keys = open('1.txt','r')
result=open('result.txt','w')
posx = 0
posy = 0
for line in keys:
    if len(line) != 18 :#忽略空行
         continue
    x = int(line[6:8],16)
    y = int(line[9:11],16)
    if x > 127 :
        x -= 256
    if y >120 :#这个参数控制单个字符的高度，如果高度过大导致字符过瘦，请调大
        y -=264#这个参数控制字符串的倾斜程度，如果向下倾斜就调高，如果向上倾斜就调低
    posx += x
    posy += y
    btn_flag = int(line[3:5],16)  # 1 for left , 2 for right , 0 for nothing
    if btn_flag == 1 :
        result.write(str(posx)+' '+str(-posy)+'\n')
keys.close()
result.close()
```

## 字符串去空格

``` python
a = input("输入字符串:")
b = "".join(a.split())
print("\n")
print(b)
```

## RSA

### RSA 求d

```python
import gmpy2

p = 7899138624562052067738543028818282791207
q = 12125717737288226389
e = 236515

d = int(gmpy2.invert(e , (p-1) * (q-1)))

print(d)
```

### RSA  计算出明文 并且将其转为字符串

```python
import rsa
p = 7899138624562052067738543028818282791207
q = 12125717737288226389
n = 95782725329150598816862723656993817444538004124649434561523
e = 236515
d = 10826463071377398188992407125262853380796488863323522719421
privatekey = rsa.PrivateKey(n , e , d , p , q) #根据已知参数，计算私钥
with open("flag.enc" , "rb") as f:
 print(rsa.decrypt(f.read(), privatekey).decode()) #使用私钥对密文进行解密，并打印
```



# 爬虫

## 常用

### 下载网页内容

```python
import requests

def get_url(url):
    # 代理
    # proxies = {"http": "127.0.0.1:10808", "https": "127.0.0.1:10808"}
    headers = {'user-agent': 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2987.98 Safari/537.36'}
    # res = requests.get(url, headers=headers, proxies=proxies)
    res = requests.get(url, headers=headers)
	
    return res

def main():
    url = input("请输入链接地址：")
    res = get_url(url)

    with open("网页内容.txt", "w", encoding="utf-8") as file:
        file.write(res.text)
    
if __name__ == "__main__":
    main()
```



## 爬取豆瓣电影top250

### 第一版

缺点 只能爬取第一个界面

```python
import requests
from bs4 import BeautifulSoup

headers = {
    # 伪装成谷歌浏览器
    'User-Agent': 'Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.12 Mobile Safari/537.36',
}
r = requests.get("https://movie.douban.com/top250",headers = headers)
r.encoding = r.apparent_encoding

# 找到位置
soup = BeautifulSoup(r.text,"lxml")
title = soup.find_all("div",class_="hd") 

# 对数据进行排行并保存
count = 1       #计算电影的排名数          
with open(r"doubanTOP250.txt",'w') as f:
    for each in title:
        each2 = (str(count) + "." + each.a.span.text+"\n")
        count += 1
        f.write(each2)
```

### 第二版

```python
import requests
from bs4 import BeautifulSoup

#开打连接
def open_url(url):
    headers = {
        # 伪装成谷歌浏览器
        'User-Agent': 'Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.12 Mobile Safari/537.36',
    }
    res = requests.get(url,headers = headers)
    res.encoding = res.apparent_encoding
    return res
# 查找数据
def find(res):
    # 找到各数据位置位置
    soup = BeautifulSoup(res.text,"lxml")
    # 电影名
    title = []
    targets = soup.find_all("div",class_="hd") 
    for each in targets:
        title.append(each.a.span.text)
    # 排名
    top = []
    targets = soup.find_all("div",class_="pic") 
    for each in targets:
        top.append(each.em.text)
    # 评分
    score = []
    targets = soup.find_all("span",class_="rating_num")
    for each in targets:
        score.append(each.text)
    # 评分人数
    scorenum = []
    targets = soup.find_all("div",class_="star")
    for each in targets:
        scorenum.append(each.text.split("\n")[4])
    # 类别
    category = []
    targets = soup.find_all("p",class_="")
    for each in targets:
        category.append(''.join(each.text.split("\n")[2].strip().split("\xa0")))
    # 组合起来
    result = []
    num = len(top)
    for i in range(num):
        result.append(top[i]+"."+title[i]+"\n    "+score[i]+"分 "+scorenum[i]+"\n    "+category[i]+'\n\n')
    return result
# 获取其他页面的URL
def url1(res):
    soup = BeautifulSoup(res.text,"lxml")
    try:
        for each in soup.find_all("span",class_="next"):
            url = ("https://movie.douban.com/top250"+each.find("a").get("href"))
        return url
    except:
        return 0
    

url = "https://movie.douban.com/top250"
res = open_url(url)
result = find(res)
# 爬取多个页面
while True:
    url = url1(res)
    if url == 0 :
        break
    else:
        res = open_url(url)
        result.extend(find(res))
    
# 数据保存       
with open(r"豆瓣电影 Top 250.txt",'w') as f:
    for each in result:
        f.write(each)
```



## 爬取煎蛋妹子图

数据保存在当前目录下girlphoto文件（需要手动创建）

```python
from bs4 import BeautifulSoup
import requests
import urllib.request

#获取url页面下的信息
def open_url(url):
    headers = {
        "User-Agent":"Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:78.0) Gecko/20100101 Firefox/78.0",
        "referer":"http://jandan.net/"
        }
    res = requests.get(url,headers = headers)
    res.encoding = res.apparent_encoding
    return res
#寻找需要的图片链接
def find(res):
    
    soup = BeautifulSoup(res.text,"lxml")
    for each in soup.find_all("a",class_=("view_img_link")):
        urllist.append("http:" + each.get('href'))
    return urllist
#寻找下一个url的地址
def url_(res):
    soup = BeautifulSoup(res.text,"lxml")
    try:
        for each in soup.find_all("a",class_="previous-comment-page"):
            url = ("http:"+each.get("href"))
        return url
    except:
        return 0

host = "http://jandan.net/ooxx"	#主界面地址
res = open_url(host)	#打开主界面
urllist = find(res)		#找到当前页面下的妹子图片链接 并保存

while True:
    url = url_(res)
    if url == 0 :
        break
    else:
        res = open_url(url)
        urllist.extend(find(res))

# 找到所有网页的地址 接下来进行爬取并且保存数据


for each in urllist:
    response = urllib.request.urlopen(each)
    name = each.split("/")[-1]
    with open("./girlphoto/"+name,'wb') as f:
        f.write(response.read())
        print(name)

```

