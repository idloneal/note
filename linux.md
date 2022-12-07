# 命令

| tough                                       | 创建文件                                                     |
| ------------------------------------------- | ------------------------------------------------------------ |
| mv a aa                                     | 将文件名a改成aa   若aa为目录则将文件a移到aa里  且 若aa后面跟/x 则将重命名为x |
| mkdir                                       | 创建目录                                                     |
| cat                                         | 查看文件内容                                                 |
| more                                        | 查看文件内容但只能往下看                                     |
| less                                        | 分页显示文件内容                                             |
| head                                        | 查看文件首（默认前10 或加命令- num 变为查看num行）           |
| tail                                        | 查看文件尾（同上）                                           |
| pwd                                         | 显示当前的绝对路径                                           |
| wget                                        | 下载文件                                                     |
| xdg-open                                    | 在浏览器打开文件                                             |
| date - R  \| timedatectl status             | 查看当前时间状态                                             |
| netstat                                     | 端口                                                         |
| less                                        | 类似vim查看                                                  |
| uname                                       | 查看系統版本                                                 |
| sudo apt-get  install language-pack-zh-hans | 安装简体中文                                                 |
| find / -name v2ray                          | 查看v2ray文件存储位置  \|asd\|asd\|                          |

# 一些好用的工具

## zsh 

### **zsh-syntax-highlighting插件**

## tmux

## 软件安装

* 源码
  绝大多数开源软件都是以源代码形式发布的，源代码一般会被打包成tar.gz的归档压缩文件，程序源代码需要<font color=#FF0000 >编译</font>成为二进制形式之后才能够运行使用。虽然源代码形式的软件使起来较为 麻烦，但是兼容性及可控制性较好。
*  源代码基本安装流程 

  * ./configure			进行软件配置．开启功能、调整安装目录、工作目录 
  
  * make					进行编译，make命令会根据当前软件开发时的语言，自动识别跟调用相 ·make 应的编译器，进行二进制编译 
  
  * makeinstaIl				进行软件的安装（设置启动文件、移动执行文件） 
* apt-get包管理工具
  *  -install联网安装软件
  *  -remove卸载

