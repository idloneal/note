# C语言基础

## 两个整数加法

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int a,b,sum;
	printf("本程序为加法程序 请依次输入两个整数 回车运行\n");
	system("color f1");
    
	printf("---------------------------\n");
	printf("请输入第一个整数\n");
	scanf("%d",&a);
	system("color f3");
	printf("请输入第二个整数\n");
	system("color ff");
	scanf("%d",&b);
    
	sum=a+b;
	system("color f4");
	printf("sum=%d\n",sum);

	return 0;
}
```

## 求最大值

### 第一版  三个整数最大值

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int a,b,c,max;
	system("color f4");
    
	printf("请输入三个整数\n");
	scanf("%d%d%d",&a,&b,&c);
	
    if (a>b) max=a;
		else max=b;
	if (c>max) max=c;
	
    printf("max=%d\n",max);
	
    return 0;
}
```

### 第二版    求n个数最大值（n需要自己修改）

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	double i,a,max=-9999999999;
	system("color 0a");
	
	for(i=1;i<=3;i++)
	{
		printf("输入一个数\n");
		scanf("%lf",&a);
		if(a>max) max=a;
	}	
	printf("最大值为%lf",max);
	return 0; 
 }
```

### 第三版

```c
#include <stdio.h>
#include <stdlib.h>

int smax( int x,int y );

int main()
{
	system("color 0a");
	int a,max=-999999999;
	
	printf("输入数字用空格隔开\n");
	 
	while(1)
	{
		scanf("%d",&a);
		max=smax(a,max);
		if( getchar()=='\n' )
		break;
	}
	printf("最大值为%d",max); 
	 
	return 0;
}
int smax( int x,int y )
{
	return(x>y? x:y);
}
```



## 求三个整数的绝对值的平均值

### 第一版

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int a,b,c,vs;
    system("color f4");
	printf("输入三个整数\n");
	scanf("%d%d%d",&a,&b,&c);
    
	vs=(abs(a)+abs(b)+abs(c))/3;
	printf("平均值=%d\n",vs);
    
	return 0; 
}
```

### 第二版

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int a,b,c;
	float vs;
	printf("输入三个整数\n");
	system("color f4");
	scanf("%d%d%d",&a,&b,&c);
    
	vs=(abs(a)+abs(b)+abs(c))/(float)3;
	printf("平均值=%f\n",vs);
	return 0; 
}
```

## 查看整数类型的字节数

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	_int64 a;
	printf("输入你想要查看的类型有多少字节\n");
		system("color f4");
    scanf("%d",&a);
	printf("的字节数为=%d\n",sizeof(a));
    
	return 0;
}
```

## 互换a和b的值

### 第一版


```C
  #include<stdio.h>
  #include<stdlib.h>
  int main()
  {
  int a=66,b=99;
   
  b=a-b;
  a=a-b;
  b=b+a;//把a与b的值互换。
   
  printf("a=%db=%d\n",a,b);
   
  return 0;
  }
```

### 第二版  位运算

```c 
#include<stdio.h>
#include<stdlib.h>

int main()
{
	system("color 0a");
	
	int a=66,b=99;
	
	b=a^b;
	a=b^a;
    b=a^b;
    
	printf("a=%d b=%d\n",a,b);

	return 0;
}
```



## 十进制转换器

```c
#include<stdio.h>
#include<stdlib.h>
void butler(void);
int i;
int main(void)
{
    system("color f4");
    printf("输入你想要转的数字")
    scanf("%d",&i);
    
    printf("=%d\n"
           "八进制=%o\n"
           "十六进制=%x\n\n",i,i,i);
    
    printf("按下Enter显示各进制数的前缀\n");
	getchar();
	getchar();
    butler();
    return 0;
}
void butler(void)
{
    printf("十进制=%#d\n"
           "八进制=%#o\n"
           "十六进制=%#x\n",i,i,i);
	system("color f3");
		getchar();
}
```

## 四则运算

### 第一版

 ```c
   #include<stdio.h>
   #include<stdlib.h>
   int main(void)
   {
   	float a,b;
   	system("color f4");
       
   	printf("输入两个实数\n");
   	scanf("%f%f",&a,&b);
   	printf("a+b=%f\n"
   	   	   "a-b=%f\n"
   		   "a÷b=%f\n"
   		   "a×b=%f\n",
   		   a+b,a-b,a/b,a*b);	
   	getchar();
   	getchar();
   	return 0;
   }
 ```
### 第二版

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	float num_1,num_2,result;
	char oper_ch=0;
	system("color f4");
    
	printf("依次输入数字运算符数字");
	scanf("%f%c%f",&num_1,&oper_ch,&num_2);

	if(oper_ch=='+') result=num_1+num_2;
	if(oper_ch=='-') result=num_1-num_2;
	if(oper_ch=='*') result=num_1*num_2;
	if(oper_ch=='/') result=num_1/num_2;
	printf("=%f\n",result);
}
```

### 第二版plus

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	system("color f4");
	
	float num1,num2,sum;
	char c1;
    
	printf("依次输入数字运算符数字");
	scanf("%f%c%f",&num1,&c1,&num2);
	
	switch(c1)
	{case'+':sum=num1+num2;break;
	 case'-':sum=num1-num2;break;
	 case'*':sum=num1*num2;break;
	 case'/':sum=num1/num2;break;
	}
    
    printf("%f",sum);
    
    return 0; 
 }
```

### 第三版

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	float num1,num2,sum;
	char c1;
	
	system("color 0a");
	
	while(1)
	{
		printf( "----选择菜单----\n"
				"****************\n"
				"*1.计算  2.退出*\n"
				"****************\n");
		scanf("%c",&c1);
		getchar();
	
	if(c1=='1')
		while(1)
			{{{printf("依次输入数字1 运算符号 数字2\n");
			scanf("%f%c%f",&num1,&c1,&num2);
		
			if (c1=='+' || c1=='-' || c1=='*' || c1=='/')
				{switch(c1)
					{
					case'+':sum=num1+num2;break;
				 	case'-':sum=num1-num2;break;
					case'*':sum=num1*num2;break;
				 	case'/':sum=num1/num2;break;
					}
 	 	  		printf("%f\n",sum);getchar();getchar();break;} 
			else
				{printf("请输入有效值\n\n");getchar();}}}}
				
	if(c1=='2')
        {
    	 printf("确定退出？（Y/N）\n");
    	 scanf(" %c",&c1);
    	 getchar();
    	 if (c1=='Y' || c1=='y')
    	{printf("感谢您的使用！\n");exit(0);}
		}
	
	else
		{printf("请输入正确的指令\n\n");} 
	} 
	return 0; 
 }
```



##  查看ACSii码

```c
#include<stdio.h>
#include<stdlib.h>
int main(void)
{
	int a;
	char c1;
	unsigned c2;
	system("color f4");
    
    printf("输入你要查看的acsii码");
	scanf("%d",&a);
    
	c2=a,c1=a;
    
	printf("输出c:%c,%d\n",c1,c1);
	printf("输出c:%c,%u\n",c2,c2);
	return 0;
}
```

##　大小写转换

### 第一版 小写转大写

```c
#include<stdio.h>
#include<stdlib.h>
int main(void)
{
	char c1;
	system("color f4");
	scanf("%c",&c1);
    
	printf("%c\n",c1-32);
	return 0;
}

```

### 第二版 位运算

```c
#include <stdio.h>
#include <stdlib.h>

void main()
{ 
	system("color 0a");
	char ch;
	
	printf("请输入一个字母：");
	ch=getchar();
	
	while(!( (ch>='A' && ch<='Z') || (ch>='a' && ch<='z')))
	{
		setbuf(stdin, NULL);
		printf("输入有误请重新输入");
		ch=getchar(); 
	}
	( ch & 32 )?  (ch&=223):(ch|=32);
	
	printf("%c",ch);
} 

```



## 鸡兔同笼

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	system("color f4");
	int head,foot,chicken,rabbit;
    
	printf("输入鸡兔的总数目\n") ;
	scanf("%d",&head);
	printf("输入鸡兔的总脚数\n");
	scanf("%d",&foot);
    
	chicken=(head*4-foot)/2;
	rabbit=head-chicken;
    
	printf("鸡有%d只，兔子有%d只",chicken,rabbit);
	return 0;
}
```

##  求直角三角形的面积

```c 
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int a,b,c,s;
	system("color f4");
	
	printf("请输入三角形三个边的值\n");
	scanf("%d%d%d",&a,&b,&c);
	
	if((a+b)<=c || (b+c)<=a || (a+c)<=b)//求三角形规范性 
	
	printf("这不是个闭合三角形");
	else
	{
		if(a>=b && a>=c)//求三角形的哪两边为短边 
			s=b*c*0.5;
			else if(b>=a && b>=c)
				s=a*c*0.5;
				else
					s=a*b*0.5;		
		
		printf("三角形的面积为%d",s);
	}
	return 0; 
}
```

##  求一元二次方程的两个根

```c
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
int main()
{
	system("color f4");
	float a,b,c,x1,x2;
    
	printf("ax^2+bx+c\n");
	printf("按顺序输入一元二次方程的系数abc\n");
	scanf("%f%f%f",&a,&b,&c);
    
	if (b*b==4*a*c)
		printf("x1=x2=%d",x1=-b/(2*a));
		else 
            {if (b*b<4*a*c)
                printf("此方程无解");
                else
              		printf("X1=%f,X2=%f",x1=(-b+sqrt(b*b-4*a*c))/(2*a),x2=(-b-sqrt(b*b-4*a*c))/(2*a));	
            }
}
```

## 判断奇偶性

```c
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
int main()
{
	system("color f4");
	int a;
	scanf("%d",&a);
    
	if(a%2==0)
		printf("该数为偶数");
	else
		printf("该数为奇数");
	return 0;
}
```

## 将一个三位数反向输出

```c
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
int main()
{
	system("color f4");
	int num,a,b,c;
	printf("将一个三位数反向输出\n");
	scanf("%d",&num);
    
	c=num%10;
	b=num%100-c;
	a=(num-b-c)/100;
	num=c*100+b+a;
    
	printf("%d",num);
	return 0;
}
```

## n个数相加（整数）

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int sum,n;
	system("color 0a");
	
	printf("输入一个整数 输入0结束\n");
	scanf("%d",&n);
	
	while(n!=0)
	{	
 		sum+=n;
		printf("输入一个整数 输入0结束\n");
		scanf("%d",&n);
	} 
	printf("和为%d\n",sum);
	return 0; 
 }
```

## 求两个数的最大公约数和最小公倍数

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int m,n,GCD,LCM,y=1;
	system("color 0a");
	
	printf("输入两个整数 求最大公约数个最小公倍数\n");
	scanf("%d%d",&m,&n);
	
	for(LCM=1;LCM>0;LCM++)
		if(LCM%m==0 && LCM%n==0)break; 
	
	while(y)
	{
		y=m%n;
		printf("%d/%d （余%d）\n",m,n,y);//显示辗转相除法的过程 	
		GCD=m=n;
		n=y;
	} 
	printf("最大公约数为%d 最小公倍数为%d\n",GCD,LCM);
	return 0; 
 }
```

## 三个整数由大到小排序

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int a,b,c,t;
	system("color 0a");
	
	printf("依次输入三个整数\n");
	scanf("%d%d%d",&a,&b,&c);
	while(1)
	{
		if(a>=b && b>=c)
			{printf("%d>%d>%d",a,b,c);exit(0);}
		else
		{
			if (b>a)
				{t=a;a=b;b=t;}
			if (c>b)
				{t=b;b=c;c=t;}
		}
	}		
	return 0; 
}
```

## 九九乘法表

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int i,j,a;
	system("color 0a");
	
	for(i=1;i<10;i++)
		{for(j=1;j<10;j++)
			{if(i>=j)
				printf("%dx%d=%-2d\t",i,j,i*j);
			}
			printf("\n");
		}
		return 0; 
}
```

## 统计字符串个数

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    system("color 0a");
	int i=0,j=0,k=0,a;								
	char c;
	
	printf("输入你想查看的字符串\n");
	
	while(1)
	{
		scanf("%c",&c);
		
		if(c=='\n')
			{printf("是否结束输入  \n Y/y确认\n");
			scanf("%c",&a);
			getchar();//吞输入的回车 
			
			if( a=='y' || a=='Y' )
				break;
			else
				printf("请继续输入\n") ;
		}
		
		if ( c>=48 && c<=57)
			i++;
		else if ( c>=9 && c<=12 || c==' ' )
			j++;
		else
			k++;
		
	}
	printf("有%d个数字 %d个空白符 %d个其他字符",i,j,k); 
}
```

## 投票系统

### 第一版

```c
#include <stdio.h>
#include <stdlib.h>  
 
int main() 
{
	system("color 0a");
	
	int T;
	int i,j;
	char name[20];
	
	struct 
	{
		char *name;
		int count;
	}num[4]={
				{"甲",0},
				{"乙",0},
				{"丙",0},
			};
	printf("候选人有 甲 乙 丙\n");
	
	T=10;//轮回数 
	while(T--)
	{
		printf("第%d票投给 ",10-T);
		scanf("%s",name); 
	
		//判断给了几票 
		if(strcmp(name,"甲")==0)
		{
			num[0].count++;
		}
		if(strcmp(name,"乙")==0)
		{
			num[1].count++;
		} 
		if(strcmp(name,"丙")==0)
		{
			num[2].count++;
		}
	}
	//显示每个人都有几票 
	for(i=0;i<3;i++)
	{
		printf("%s的票数为%d\n",num[i].name,num[i].count);
	}
	//求最大值
	for(j=0;j<3;j++)
	{
		for(i=0;i<3;i++)
		{
			if(num[i+1].count>num[i].count)
			{
				num[4].count=num[i].count;
				num[i].count=num[i+1].count;
				num[i+1].count=num[4].count;
				num[4].name=num[i].name;
				num[i].name=num[i+1].name;
				num[i+1].name=num[4].name;
			}
		}
	}
	printf("%s的得票最高为%d票\n",num[0].name,num[0].count);
}	
```

### 第二版

```c
#include <stdio.h>
#include <stdlib.h>  

int main() 
{
	system("color 0a");
	
 	int i=0,j=0,k=0;
 	int T=10;
 	char name[20];
 	
 	printf("候选人名字为 甲 乙 丙\n");
 	
	while(T--)
	{
		printf("请输入%d号支持的人\n",10-T);
		scanf("%s",&name);
		if(strcmp(name,"甲")==0)
			i++;
		else if(strcmp(name,"乙")==0)
			j++;
		else if(strcmp(name,"丙")==0)
			k++;
	}
	printf( "甲为%d票\n"
			"乙为%d票\n"
			"丙为%d票\n",i,j,k);
	
	if(i>=j && i>=k)
	{
		printf("甲的得票最多为%d票\n",i);
	}
	if(j>=i && j>=k)
	{
		printf("乙的得票最多为%d票\n",j);
	}
	if(k>=j && k>=i)
	{
		printf("丙的得票最多为%d票\n",k);
	}
    return 0;
}	
```

## 成绩统计

### 第一版

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>  
 
struct student
{
	long num;
	float score;
	struct student *next;
};

int main()
{
	system("color 0a");
	
	int n=0;
	
	struct student p[1000],*head;
	
	printf("本程序为统计成绩\n");
	printf("输入学号 与 成绩\n学号输入为0终止此程序\n");
	scanf("%d%f",&p[n].num,&p[n].score);
	
	while(1)
	{
		if(p[n].num==0)
		{
			p[n-1].next=NULL;
			break;
		}
		n++;
		
		if(n==1)//判断是不是第一个 
		{
			head=&p[0];//p0的值给head 
			p[0].next=&p[1];//p0的下一个为p1的地址 
		} 
		else                         
		{
			p[n-1].next=&p[n];
		}
		printf("输入学号 与 成绩1\n");
		scanf("%d",&p[n].num);
		if(p[n].num!=0)
		{
			scanf("%f",&p[n].score);	
		}
	}
	do
	{
		printf("学号 %d分数 %.1f\n",head->num,head->score);
		head=head->next;
	}while( head );
	return 0;
}
```

### 第二版

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>  
 
struct student
{
	long num;
	float score;
	struct student *next;  //创建链表
}; 

int main()
{ 
	system("color 0a");
	
	int n=0;
	int a,b;
	int i;
	
	struct student p[1000],*head;
	
	printf("本程序为统计成绩\n");
	printf("输入学号 与 成绩\n学号输入为0终止此程序\n");
	scanf("%d%f",&p[n].num,&p[n].score);
	
	while(1)
	{
		if(p[n].num==0)
		{
			p[n-1].next=NULL;
			break;
		}
		n++;
		
		if(n==1)//判断是不是第一个
		{
			head=&p[0];//p0的值给head
			p[0].next=&p[1];//p0的下一个为p1的地址
		} 
		else                         
		{
			p[n-1].next=&p[n];
		}
		printf("输入学号 与 成绩\n");
		scanf("%d",&p[n].num);
		if(p[n].num!=0)
		{
			scanf("%f",&p[n].score);	
		}
	}
	
	do
	{
		printf("学号 %d分数 %.1f\n",head->num,head->score);
		head=head->next;
	}while( head );
	
	printf("输入你要删除的学号\n");
	scanf("%d",&a);
	
	for(i=0;i<=1000;i++)
	{
		if(p[i].num==a)
		{
			p[i-1].next=&p[i+1];
		} 
		if(p[i].next==NULL)
		{
			p[i-1].next=NULL;
		} 
	}
	
	head=&p[0];//让head指向第一个 
	
	do
	{
		printf("学号 %d分数 %.1f\n",head->num,head->score);
		head=head->next;
	}while( head );
	return 0;
}
```

## 在原处创建一个文件并且写入

```c
#include <stdio.h>
#include <stdlib.h>

void main()
{ 
	system("color 0a");
		
	FILE *fp;
	char ch,filename[20];
	
	printf("输入你要创建的文件名:");
	scanf("%s",filename);
	
	fp=fopen(filename,"wt+");
	
	printf("输入你想要写入的内容:");
	ch=getchar();
	ch=getchar();
	while( ch!=EOF )
	{
		fputc( ch,fp );
		ch=getchar();
	}
	
	fclose(fp);
}
```

# 实例

## 猴子吃桃问题

​	猴子第一天摘下若干个桃子，当即吃了一半，还不过瘾，又多吃了一个。
​	第二天早上又将第一天剩下的桃子吃掉一半，又多吃了一个。
​	以后每天早上都吃了前一天剩下的一半零一个。
​	到第 n 天早上想再吃时，发现只剩下一个桃子了。
​	编写程序求猴子第一天摘了多少个桃子。

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int a=1,i,day;
	system("color 0a");
	
	printf("请输入猴子第几天吃完？\n");
	scanf("%d",&day);
	
	for(i=day-1;i>0;i--)
		a=(a+1)*2;
		
		printf("猴子一共采摘了%d个桃子",a);	
		return 0;		 
}
```

## 百钱买鸡

​	中国古代数学家张丘建在他的《算经》中提出了一个著名的“百钱买百鸡问题”，
​	鸡翁一，值钱五，鸡母一，值钱三，鸡雏三，值钱一，百钱买百鸡，问翁、母、雏各几何？ 

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	int JW,JM,JC;
	system("color 0a");
	
	for(JW=0;JW<20;JW++)
		{for(JM=0;JM<33;JM++)
			{for(JC=0;JC<100;JC++)
			if((JW+JM+JC)==100 && (JW*5+JM*3+JC/3.)==100)
			printf("鸡翁有%d个  鸡母有%d个  鸡雏有%d个\n",JW,JM,JC); 
			}
		}
	return 0;		 
}

```

##  渔夫打鱼晒网问题

​	如果一个渔夫从2011年1月1日开始每三天打一次渔，两天晒一次网，
​	编程实现当输入2011年1月1日以后的任意一天，输出该渔夫是在打渔还是在晒网。

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
	system("color 0a");
	int year,month,day,a=0,b=0,i,j,k,l,
	s[2][13]={0,0,31,29,31,30,31,30,31,31,30,31,30,
			  0,0,31,28,31,30,31,30,31,31,30,31,30};
	
    printf("依次输入年月日\n");
	scanf("%d%d%d",&year,&month,&day);
	
	for(i=2011;i<year;i++)//计算出到那年有多少天 
		{if(i%4==0 && i%100!=0 || i%400==0)
			a+=366;
		else 
			a+=365;
		}
	
	for(j=1;j<=month;j++)//计算出到那个月有多少天
		{if (year%4==0 && year%100!=0 || year%400==0)//判断今年是不是闰年 
			l=0;
		else
			l=1;
		a+=s[l][j];
		}
	a+=day;
	
	printf("过了%d天",a);
    if(a%5<4)
    	printf("这天在打鱼");
	else
	 	printf("这天在晒网"); 
	
	return 0;		 
}
```

## 二分查找法

本实例采用二分查找法查找特定关键字的元素。
要求用户输入数组长度，也就是有序表的数据长度，并输入数组元素和査找的关键字。
程序输出查找成功与否，以及成功时关键字在数组中的位置。
例如，在有序表 11、13、18、 28、39、56、69、89、98、122 中査找关键字为 89 的元素。 

```c
#include<stdio.h>
#include<stdlib.h>

int er_feng_fa(int key,int T,int a[])
{
	int count=0,low,high,mid;
	low=0;
	high=T-1; 
	
	if(key>=a[T-1] || key<=a[0])//确保一开始就在范围内 
	printf ("查找失败");
	 
	while(low<high)  //当不在查找范围内的时候退出循环 
	{
		count++;  //查找了几次 
		mid=(low+high)/2;//确定中间值 
		if(key<a[mid])
		{
			high=mid-1; //使查找范围为此次中间值的左边,-1加快查找速度 
		} 
		if(key>a[mid])
		{
			low=mid+1;  //使查找范围为此次中间值的右边 
		}  
		if(key==a[mid])
		{
			printf("查找成功\n查找%d次 a[%d]=%d",count,mid,key);
			break;		
		}
	}
	if(count==1)
		printf("查找失败");
	return 0;
} 

int main()
{
	int T,key;
	int a[10000];
	int i;
	
	system("color 0a");
	
	printf("输入数组的长度\n");
	scanf("%d",&T);
	printf("请输入数组元素\n");
	
	for(i=0;i<T;i++)
	{
		scanf("%d",&a[i]);
	}
	printf("输入例要查找的元素\n");
	scanf("%d",&key);
	
	er_feng_fa(key,T,a); 
	return 0;
}
```

## 分块查找法

例如，采用分块查找法在有序表11、12、18、28、39、56、69、89、96、122、135、146、 156、256、298 
中查找关键字为 96 的元素。査找特定关键字元素个数为 15，
要求用户输入有序表各元素，程序输出査找成功与否，若成功，还显示元素在有序表中的位罝

```c
#include<stdio.h>
#include<stdlib.h>
struct index
{
	int max;//区块的最大值 
	int start;//区块的起始值 
}qukuai[4];

int qu_kuai(int key,int s[])
{
	int i,j=1;
    
	while( j<4 && key>=qukuai[j].max)//与区块的最大值对比 每个区块最大值依次递增 
		j++;	
	
	if(j==4)
	{
		printf("你输入的值不在数组内"); 
		return 0;
	}
	else
	{
		for(i=0;i<5;i++)
		{
			if(key==s[qukuai[j].start+i])
			{
				printf("查找成功，其位置是：%d",qukuai[j].start+i);
				break;
			} 
			if(i==5)
			{
				printf("查找失败");
				break;
			}
		}
	}
}

int main()
{
	int i,s[16],j=0;
	int key;
	
	system("color 0a");
	
	printf("请输入15个数\n");
	for(i=1;i<16;i++)
	{
		scanf("%d",&s[i]);
	}
	for(i=1;i<4;i++)
	{
		qukuai[i].start=j+1; //确定每个区块起始值
		qukuai[i].max=s[j+=5];       //确定每个区块的最大值 
	}
	
	printf("请输入你想査找的元素：");
	scanf("%d",&key);
	
	qu_kuai(key,s);
	return 0;
} 
```

## 回文素数

任意的整数，当从左向右读与从右向左读是相同的，
且为素数时，称为回文素数。求 1000 以内的所有回文素数。

```c
#include<stdio.h>
#include<stdlib.h>

int sushu(int a)
{
	int i;
	
	for(i=a-1;i>1;i--)
	{
		if(a%i==0)
		{
			return 0;
		}
	}
	return 1;
}

int main()
{
	int i;
	
	system("color 0a");
	
	for(i=2;i<=1000;i++)
	{
		if(sushu(i)==1)
		{
			if(i/100==0)
			{
				if((i%10)==(i/10))
				{
					printf("%d  ",i);
				}
			}
			else
			{
				if((i%10)==(i/100))
				{
					printf("%d  ",i);
				}
			}
		} 
	}
	return 0;
}
```

## 兔子生兔子问题

假设一对兔子的成熟期是一个月，即一个月可长成成兔，
那么，如果每对成兔每个月都生一对小兔，一对新生的小兔从第二个月起就开始生兔子，
试问从一对兔子开始繁殖，以后每个月会有多少对兔子?

```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
	int t,csq,ynq=0,month;//成熟期 幼年期 
	int i;
	
	system("color 0a");
	
	printf("一开始有多少对兔子\n");
	scanf("%d",&csq);
	
	printf("请输入你要查看的月份数\n");
	scanf("%d",&month); 
	
	for(i=1;i<month;i++)
	{
		t=csq;  //这个月生的小兔子数 
		csq+=ynq;//上个月的小兔兔成熟了   下个月成熟的数量 这个月一共的兔子数量
		ynq=t;
	}
	printf("第%d 月的兔子数为%d",month,csq);
	return  0;
}
```

## 狼追兔子

一只兔子躲进了 10 个环形分布的洞的某一个，
狼在第一个洞没有找到兔子，就隔一个洞，到第三个洞去找，也没有找到，就隔两个洞，到第六个洞去找，
以后每次多隔一个洞 去找兔子……这样下去，结果一直找不到兔子，
请问：兔子可能躲在哪个洞中？  

```c
#include<stdio.h>
#include<stdlib.h>

int cf(int a,int s[])
{
	int i;
	
	for(i=0;i<100;i++)
	{
		if(a==s[i])
		return 1;
		else if(a==10)
		return 1;
	}
	return 0;
}
int main()
{
	int i,j,sum=0,s[100]={0};

	system("color 0a");
		
	for(i=0;i<100;i++)
	{
		sum+=i;
		s[i]=sum%10;
	}
	
	for(i=1;i<11;i++)
	{
		if(cf(i,s)==0)
		printf("兔子可能藏在第%d个洞中\n",i);
	}
	return 0;
}
```

# 2019蓝桥杯

## 数字游戏

​	E星球的雷某在玩一个游戏、其下规则如下：
​	给出一堆无序整数，求解这堆整数里是否有两个数加起来刚好等于整数X，如果有回答T，没有则回答F。 
【输入】
​	第一行包含一个数字N，表示有N组测试用例，其中1<=N<=50;
​	每组测试用例包含两行，
​	第一行包含两个数字M和X，其中2<=M<=100,2<=X<=65535,
​	第二行包含m个无序整数，1<=所有无序整数<=65535	

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{	
	system("color 0a");
	int M,X,N,i,k,j,a,s[M],n[M];

	scanf("%d",&a);//有几组数据 
	
	for(i=0;i<a;i++)//确定输入数字 
	{
		n[i]=0;//使n数组的值为0 
		scanf("%d%d",&M,&X);
		for(j=0;j<M;j++)
		{
			scanf("%d",&s[j]);
		}
		for(k=0;k<M;k++)
		{
			for(j=0;j<M;j++)
			{
				if(j!=k)
					if((s[k]+s[j])==X)
						n[i]=1;
			}
		}	
	}
	for(i=0;i<a;i++)
	{
		if(n[i]==0)
			printf("F\n");
		else
			printf("T\n");
	}
	return 0;
}

```

## 命运2

​		第一行输入一个数字T，表示有T组测试用例，其中1<=T<=100;
​		每组测试用例包含两行：第一行包含两个整数N和X，表示有N个泰坦战士 和 猩红帝国剩余血量X。其中20<=N<=200,1<=X<=65535;
​		第二行包含N个整数，表示各个泰坦的战斗力，其中1<=战斗力<=1000;  
【输出】 
​		对于每组测试用例输出一行，包含一个整
​		数，表示需要几轮攻击才能打败猩红帝国 

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{	
	system("color 0a");
	int T,N,X;
	int i;
	int sum,n;
	
	scanf("%d",&T);
	
	while(T--)//一共有几组 
	{
		sum=0;
		scanf("%d%d",&N,&X);
		for(i=0;i<N;i++)//写入各个泰坦战士的战斗力 
		{
			scanf("%d",&n);
			sum+=n;
		}
		if( sum%X==0 )
			printf("%d\n",X/sum);
		else
			printf("%d\n",X/sum+1);
	}
	return 0;	
}
```

## 五角星数

​	五角星数是指某个五位数，其每一位的五次方加起来还等于这个数，
​	例如：	对于五位数54748，5^5=3125 4^5=1024 7^5=16807 8^5=32768 加起来的和为51748
​	那么总共有多少个五角星数？他们分别为？

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{	
	system("color 0a");
	int num,a,b,c,d,e,i=0,n;
	int s[100000]={0};
	
	while(1) 
	{
		for(num=10000;num<100000;num++)
		{
			a=num%10; b=(num/10)%10; c=(num/100)%10;
			d=(num/1000)%10; e=num/10000;
			if((a*a*a*a*a+b*b*b*b*b+c*c*c*c*c+d*d*d*d*d+e*e*e*e*e)==num)
			{
				s[i]=num;n=i;i++;
			}
		}
		n=n+1;
		break;
	}
	printf("\n\t一共有%d个五角星数\n",n); 
	
	for(i=0;i<100000;i++)
		if(s[i]==0)
			continue;
		else
			printf("\t%d.%d\n",i+1,s[i]); 
	
	return 0;
 }
```

## 判断大小

​		给出两个数字，求他们之间的关系
【输入】
​		第一行包含一个整数T，表示有T组数据待测试其中1<=T<=100.每组测试用例包含两个整数x和y，其中0<=x,y<=1000。 
【输出】
​		 对于每组用例输出一行，如果x>y 输出>以此类推

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{	
	system("color 0a");
	int T;
	int x,y;
	
	scanf("%d",&T);
	
	while(T--)
	{
		scanf("%d%d",&x,&y);
		if(x>y)
			printf(">\n");
		else if(x<y)
				printf("<\n");	
			else
				printf("=\n");
	} 
	return 0;	
}
```

## 大鱼吃小鱼

【输入】
		第一行包含一个整数T，表示有T组数据待测试，其中1<=T<=100.
		每组测试用例包含两行，第一行包含一个整数N[1,100]表示有N条鱼，
		第二行包含N个整数，表示N条鱼的体型。其中第一个整数为贪吃鱼的体型。
【输出】
		对于每组测试用例输出一行，包含一个整数，为贪吃鱼能吃掉多少条鱼。

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{	 
	system("color 0a");
	
	int T;
	int N,max,sum=0,a;
	int i;
	
	scanf("%d",&T);
	
	while(T--)
	{
		scanf("%d%d",&N,&max);
		for(i=1;i<N;i++)
		{
			scanf("%d",&a);
			if(max>=a)
			{
				max=a;sum++;
			}
		} 
		printf("%d",sum);
	} 
	return 0;	
}
```



# 2019 C语言实训  创建一个通讯录系统

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define P printf
#define S scanf
 
int num = 0;			//统计一共有多少个联系人		 

typedef struct Txl		//创建链表
{	
	char name[20];
	char qq[20];
	char tel[100];
	char remarks[20];
	
	struct Txl *next;  
}TXL;
 
int print()		//显示功能 
{
	system("cls"); 	
	P("\n\n\n");
	P("\t\t\t************************************************\n");
	P("\t\t\t*------------本程序为统计通讯录----------------*\n");
	P("\t\t\t*-----------输入对应号码执行对应操作-----------*\n");
	P("\t\t\t*---------1.新建联系人   2.删除联系人----------*\n"); 
	P("\t\t\t*---------3.查看联系人   4.修改联系人----------*\n");
	P("\t\t\t*---------5.查找联系人   0.退出本程序----------*\n");
	P("\t\t\t************************************************\n");
}

int ADD(TXL *head)	//添加联系人 
{
	system("cls"); 
	char c='y';
	TXL *p = (TXL *)malloc(sizeof(TXL));
	TXL *s;
	
	p=head;
	
	while(p->next)		//判断p->next是否等于NULL
    {
        p = p->next;	//不是的话 连接链表 
    }
    
	while( c =='y' || c =='Y' )
	{
		s = (TXL *)malloc(sizeof(TXL));
		
		P("请录入信息\n");
		P("\n姓名：");
		S("%s",s->name);
		P("\nQQ号：");
		S("%s",s->qq);
		P("\n电话：");
		S("%s",s->tel);
		P("\n备注：");
		S("%s",s->remarks);
		
		 while( p->next)   //找到结尾 
        {
            p = p->next;
        }
        p->next = s; 
		s->next = NULL;		//尾插法 
		
		num++; 
		
		getchar();
		P("\n是否继续输入Y/y继续 输入任意字符退出 \n");
		S("%c",&c);	
	}
}

int CK(TXL *head)	//查看联系人 
{
	system("cls"); 
		
	TXL *q;
	q = head->next;
	
	if(q == NULL)
	{
		P("暂无数据,按任意键返回主菜单\n");
		getchar();
		getchar();
		return 1;
	}
	
	do		
	{
		P("姓名：%-15s QQ号：%-15s 电话：%-15s 备注：%-15s\n",
		q->name,q->qq,q->tel,q->remarks);
		
		q=q->next;					 
	}while(q);		//当q->next为空值时退出循环 
	
	P("\n按任意键退回主菜单");
	getchar(); 
	getchar();
}

int SC(TXL *head)	//删除联系人 
{
	int i;
	char del_name[20],a='y';
	TXL *p;
	TXL *q;
	
	while( a=='Y' || a=='y' )
	{ 
		system("cls");
		int n; 
	    p = head->next;
	    q = head;
		
		P("请输入你要删除的联系人的姓名: ");
		scanf("%s",del_name);
		getchar();
		
		for( i=0;i<num;i++ )          
		{
			if( strcmp(del_name,p->name) == 0 )		//对比是否有符合的数据 
			{
				num--;						//联系人总数减 1 
				TXL *t = p;
   				q->next = t->next;
   				P("删除成功,按任意键退回主菜单");
   				getchar();
				return 1; 
			}
			p = p->next;
			q = q->next;
		}
		P("没有找到此联系人\n");
		P("是否继续Y/N\n");
		S("%c",&a) ;
	}
}

int XG(TXL *head)	//修改联系人
{
	int i;
	char del_name[20],a='y';
	TXL *p;
	TXL *q;
	
	while( a=='Y' || a=='y' )
	{ 
		system("cls");
		
		int n; 
	    p = head->next;
		
		P("请输入你要修改的联系人的姓名: ");
		scanf("%s",del_name);
		getchar();
		
		for( i=0;i<num;i++ )          
		{
			if( strcmp(del_name,p->name) == 0 )		//对比是否有符合的数据 
			{
				P("其信息如下\n");
				P("姓名：%-15s QQ号：%-15s 电话：%-15s 备注：%-15s\n",
				p->name,p->qq,p->tel,p->remarks);
				
				P("请输入修改后的信息\n");
				P("\n姓名：");
				S("%s",p->name);
				P("\nQQ号：");
				S("%s",p->qq);
				P("\n电话：");
				S("%s",p->tel);
				P("\n备注：");
				S("%s",p->remarks);
				
				P("修改成功，按任意键返回菜单\n"); 
				getchar();
				
				return 1;
			}
			p = p->next;
		}
		P("没有找到此联系人\n");
		P("是否继续Y/N\n");
		S("%c",&a) ;
	}
}

int CZ(TXL *head)	//查找联系人
{
	int i,n;
	char name[20];
	char qq[20];
	char tel[100];
	char remarks[20];
	char a='y';
	TXL *p;
	
	p = head->next;
		
	system("cls");
	P("\n\n");
	P("\t\t\t************************************************\n");
	P("\t\t\t*---------1.按姓名查找   2.按备注查找----------*\n"); 
	P("\t\t\t*---------3.按电话查找   4.按QQ号查找----------*\n");
	P("\t\t\t*--------------0.回到主菜单--------------------*\n");
	P("\t\t\t************************************************\n");
	
	S("%d",&n);
	
	switch(n)
	{
		case 0:	
				return 1;
		case 1:
				P("输入你要查找的姓名：");S("%s",name);	
				break;
		case 2:
				P("输入你要查找的备注：");S("%s",remarks);	
				break;
		case 3:
				P("输入你要查找的电话：");S("%s",tel);	
				break;
		case 4:
				P("输入你要查找的QQ号：");S("%s",qq);
				break;
		default:
				P("输入错误请重新输入\n");sleep(1);CZ(head);												
	}
	
	getchar();
	system("cls"); 
	
	for( i=0;i<num;i++ )          
	{
		if( strcmp(name,p->name) == 0 )		//对比是否有符合的数据 
		{
			P("\n其信息如下\n");
			P("姓名：%-15s QQ号：%-15s 电话：%-15s 备注：%-15s\n",
			p->name,p->qq,p->tel,p->remarks);
			
			P("\n按任意键退回主菜单");
			getchar(); 
			return 1;
		}
		
		if( strcmp(remarks,p->remarks) == 0 )
		{
			P("\n其信息如下\n");
			P("姓名：%-15s QQ号：%-15s 电话：%-15s 备注：%-15s\n",
			p->name,p->qq,p->tel,p->remarks);
			
			P("\n按任意键退回主菜单");
			getchar(); 
			return 1;
		}
			
		if( strcmp(tel,p->tel) == 0 )
		{
			P("\n其信息如下\n");
			P("姓名：%-15s QQ号：%-15s 电话：%-15s 备注：%-15s\n",
			p->name,p->qq,p->tel,p->remarks);
			
			P("\n按任意键退回主菜单");
			getchar(); 
			return 1;
		}
			
		if( strcmp(qq,p->qq) == 0 )
		{
			P("\n其信息如下\n");
			P("姓名：%-15s QQ号：%-15s 电话：%-15s 备注：%-15s\n",
			p->name,p->qq,p->tel,p->remarks);
			
			P("\n按任意键退回主菜单");
			getchar(); 
			return 1;
		}
		p = p->next;
	}
	P("未找到该联系人\n");
	P("是否继续查找Y/N\n");
	S("%c",&a);
	
	if( a == 'y' || a == 'Y' )
		CZ(head);
	else
		return 1;	
}    

int DQ(TXL *head)	//读取数据 
{
	FILE *fp = fopen("通讯录.txt", "ab+");
 
    if (fp == NULL)
    {
        P("文件打开错误");
        
		return -1; 
    }
    
    TXL *t = head;
    
    fread (&num, sizeof(int), 1, fp); //从流中读指定个数的字符  fp为已打开的文件指针 num欲保存读取文件数据的空间 1为欲读取字符数
    
    int i;
    for (i = 0; i < num; i++)
    {
        int length;
        fread (&length, sizeof(int), 1, fp);
 
        TXL *p = (TXL *)malloc(sizeof(TXL));
        if( p == NULL )
        {
            printf("动态空间分配失败\n");
            return -1;
        }
 
        int ret = fread (p, length, 1, fp);        // 读取数据
        printf("%d\n",ret);
 
        while( t->next )
        {
            t = t->next;
        }
        t->next = p;    //找到最后一个结点，将结点p尾插进链表
        p->next = NULL;
    }
 
    fclose(fp);
    
}

int BC(TXL *head)	//保存数据 
{
	FILE *fp = fopen("通讯录.txt", "w+");
	
    if (fp == NULL)
    {
        perror ("创建失败");
        return -1;
    }
 
    fwrite(&num, sizeof(int), 1, fp);// 要写入个数
    TXL *p = head;
    
    while(p->next) //判断是否为 NULL 
    {
        p = p->next;
        int length = sizeof(TXL);//写入数据的长度
        fwrite(&length, sizeof(int), 1, fp);
        fwrite(p, length, 1, fp);//写入数据
    }
 
    fclose(fp);
}

int  main()
{   
	system("color 0a");
	
	int a;
	TXL *head = (TXL *)malloc(sizeof(TXL) * 10);
	head->next = NULL;
	
	DQ(head);
	
	while(1)
	{
		print();
		
		scanf("%d",&a);
		
		switch(a)
		{
			case 0:
					BC(head);
					P("\n\n\t\t\t感谢您使用本程序\n\n");
					return 0;
			case 1:
					ADD(head);
					break;
			case 2:
					SC(head);
					break;
			case 3:
					CK(head);
					break; 
			case 4:
					XG(head);
					break; 
			case 5:
					CZ(head);
					break;
			default:
					P("输入错误请重新输入\n");
					sleep(2);
					break; 
		}	
	}
	
	return 0;	
}
```



