# 常用命令

| update                       | 更新源                                                       |
| ---------------------------- | ------------------------------------------------------------ |
| upgrade                      | 更新                                                         |
| reboot                       | 重启                                                         |
| apt                          | 连接外部                                                     |
| su root                      | 获得root权限                                                 |
| systemctl restart networking | 重启网络服务                                                 |
| vim /etc/network/interfaces  | 配置ip                                                       |
| nslookup 需要查的域名        | 域名解析                                                     |
| dig 需要查的域名             | DNS信息收集                                                  |
| dig -x 参数IP                | [反向查域名](#反向查域名)                                    |
| whois 需要查的域名           | [查询网址域名注册信息和备案信息](#查询网址域名注册信息和备案信息) |
| tracerout 需要查的域名       | 查看经过哪些网络设备                                         |
| arping 需要查的域名          | IP转成MAC地址                                                |
| netdiscover -i etho -r IP/24 | 主动探测网络内主机-p为被动                                   |
| [hping3](#hping3)            | 对服务器进行DOS攻击                                          |
| nmap  -Ss IP                 | 对端口扫描                                                   |
| [scapy](#scapy)              | 进入scapy模块                                                |
| xdg-open                     | 图形界面打开文件                                             |
| vim  /etc/resolv.conf        | 改dns                                                        |
| ctrl+shift++                 | 放大字体                                                     |
| ctrl+-                       | 缩小字体                                                     |
| ctrl+l                       | 清屏                                                         |

# 本机kali密码

| User | passwd |
| ---- | ------ |
| kali | kali   |
| root | root.  |

# 工具用法

## 反向查域名

使用 dig -x参数  IP 反查域名

```python
	$ dig  -x 114.114.114.114
结果:
	114.114.114.114jn-addr.arpa.22 IN  PTRpublicl.114dns.comv
	注：114．114．114．114反向解忻为Ysublic1.114dns.com
```

##　查询网址域名注册信息和备案信息

1. **whois.aliyun.com**

---

2. **shodan** 

   > 技巧1：通过Shodan搜索Webcam网络摄像头设备 在搜索捱中输大"webcam"或网络象头"进行搜。
   >
   > ---
   >
   > 技巧2：Shodan搜指定IP地址
   > 在搜索框中输入net:101.200.128.35
   >
   > ---
   >
   > 技巧3：Shodan搜索指定端口
   > 在搜索框中输入port：端口号，就可以搜指定端口我们可以尝一些常用端口来进行搜索
   > 比如说我们搜索80端口我们可以随便点开一个看一下页面

##　hping3

对xuegod.cn进行压力测试，
hping3 -c 1000 -d 120 -S -w 64 -p 80 flood --rand-source xuegod.cn
参数
-c 1000  =	发送的数据包的数量。
-d120 	=	发送到目标机器的每个数据包的大小。单位是字节
-S		   =	只发送SYN数据包。
-w64	  =	TCP窗口大小。
-P80	  =	目的地端口（80是WEB端口）。你在这里可以使用任何端口。
--flood	=	尽可能快地发送数据包不需要考虑显示入站回复。洪水攻击模式。
--rand-source	=	使用随机性的源头地址。这里的伪造的地址，只是在局域中伪造。通过路由器后，还会还原成真实的IP地址。

---

## scapy

### scapy的使用方法：
我们使用ARP().display()查看ARP函数的用法，

---

> hwtype = 0x1			  硬件类型。
> Ptype = 0x800			协议类型
> hwlen = 6					硬件地址长度（MAC)
> plen = 4					   协议地址长度（）
> op = who-has			  who-has查
> hwsrc = 00:Oc:29:6a:cf:Id		 源MAC地址
> psrc=192.168.1.53					源IP地址
> hwdst=00:00;00;00;00;00		 目的MAC地址
> pdst=0.0.0.0							  目的IP地址址，向谁发送查询请求

: srl函数作用: 发送数据包和接受数据包的功能
		例：使用srl函数生成一个ARP包。询问192.168.1.1的MAC地址为多少

```python
$ srl(ARP(pdst="192.168.1.1"))
```

​		注:IP()生成ping包的原IP和目标IP，ICMP()生ping包的类型。使用IP()和ICMP()两个函数，可以生成ping包，进行探测

---

思路

 1. 修I P 包头的dst，也就是我们的目的地址

 2. 拼接上ICMP的數据包类型．

 3. 使用srl进行发送數据包接收數据包

---

sr1(IP(dst=192.168.1.1')/TCP(flags='S‘，dport=80),timeout=1)
    flags="S"示SYN数据包
    dport=80表示目标端口80

---

### scapy定制UDP协议 

和我们构造TCP数据包的方式一样，我们使用UDP的协议进行探测，但是UDP协议是不可靠的。

 探测的标准：<font color=#FF0000 >没有收到回应包，表示端口开放。收到回应包，表示UDP端口关闭或此端口是非UDP端口。</font>

 查看UDP（）使用方法

```python
$ UDP().display()
###[UDP]###
	spon=domaln
   	clpon=domain
    len=None
    chksum=None
```

## WPScan

1. Wordpress 版本检测和主题检测
2. Wordpress 插件安全检测
3. 密码的暴力破解
4. 可以指定代理

---

| wpscan --url  url                                           | 扫描wp漏洞           |
| ----------------------------------------------------------- | -------------------- |
| wpscan --url url --enumerate u                              | 扫描wp用户           |
| wpscan --url url --enumerate t                              | 扫描主题             |
| wpscan --url url --enumerate vt                             | 扫描主题的漏洞       |
| wpscan --url url --enumerate vp                             | 扫描插件的漏洞       |
| wpscan --url url -e u  --wordlist   /root/桌面/password.txt | 用wpscan进行暴力破解 |

## **msfconsole**

**终端输入msfconsole进入系统**

---

### **history**

显示之前输入的命令

---

### **show** 

​	(模块名称) 展示某个模块的信息 

​	all  所有模块

> msf5 > show exploitse 
> #列出 metasploit 框架中的所有渗透攻击模块。改命令列出的数据较多,<font color=#ff0000>较为耗时间</font> 
> msf5 > show payloads metasploit  #列出所有攻击载荷
> msf5 > show auxiliary metasploit   #列出所有辅助攻击载荷

---

### **search**

查找漏洞

name:    通过名称进行查找

path:    	通过路径进行查找

platform: 影响此平台的模块

type:     	特定类型的模块 （exploits payloads…）

上面的命令和进行组合联合查找 例如

search type:auxiliary name:mysql 

>​	<font color=#ff0000>Rank 按 照 可 靠 性 降 序 排 列 :</font> 
><font color=#ff0000>	excellent</font> 	漏 洞 利 用 程 序 绝 对 不 会 使 目 标 服 务 崩 溃 ， 就 像 SQL 注 入 、 命 令 执 行 、 远 程 文 件 包 含 、 本 地 文 件 包 含 等 等 。 除 非 有 特 殊 情 况 ， 典 型 的 内 存 破 坏 利 用 程 序 不 可 以 被 评 估 为 该 级 别 。 
><font color=#ff0000>	great </font>	该 漏 洞 利 用 程 序 有 一 个 默 认 的 目 标 系 统 ， 井 且 可 以 自 动 检 测 适 当 的 目 标 系 统 ， 或 者 在 目 标 服 
>务 的 版 本 检 查 之 后 可 以 返 回 到 一 个 特 定 的 返 回 地 址 。 
><font color=#ff0000>	good</font> 	该 漏 洞 利 用 程 序 有 一 个 默 认 目 标 系 统 ， 共 且 是 这 种 类 型 软 件 的 " 常 见 情 况 （ 桌 面 应 用 程 序 的 
>Windows 7 ， 服 务 器 的 2012 等 ） 
><font color=#ff0000>	normal </font> 	该 漏 洞 利 用 程 序 是 可 靠 的 ， 但 是 依 赖 于 特 定 的 版 本 ， 荇 且 不 能 或 者 不 能 可 靠 地 自 动 检 测 。 
><font color=#ff0000>	average </font> 	该 漏 洞 利 用 程 序 不 可 靠 或 者 难 以 利 用 。 
>​	<font color=#ff0000>low </font>	对 于 通 用 的 平 台 而 言 ， 该 漏 洞 利 用 程 序 几 乎 不 能 利 用 （ 或 者 低 于 50 ％ 的 利 用 成 功 率 ） 
><font color=#ff0000>	manual</font> 	该 漏 洞 利 用 程 序 不 稳 定 或 者 难 以 利 用 井 且 基 于 拒 绝 服 务 (DOS). 如 果 一 个 模 块 只 有 在 用 户 
>特 别 配 置 该 模 块 的 时 候 才 会 被 用 到 ， 否 则 该 模 块 不 会 被 使 用 到 ， 那 么 也 可 以 评 为 该 等 级 。 

### **info**

模块的详细信息

---

### **use**

​	**使用/加载模块**

​	back      退出加载的模块

​	info       当前模块的详细信息

​	show targets 可用于哪个系统

​	run -j     攻击后将其保存到后台

​	session    查看后台

​	session -i 2 继续运行2号后台

​	session -k 2 终止2号后台

​	**攻击成功后**

​		backgroud 将当前进程保存到后台

​		exit       退出当前进程