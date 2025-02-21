











# 2021年10月日

1. 英文转中文的关键词查询

   

2. 待定

# 2021年10月日

1. 英文转中文的关键词查询

   

2. 待定

# 2021年10月日

1. 英文转中文的关键词查询

   

2. 待定

# 2021年10月日

1. 英文转中文的关键词查询

   

2. 待定

# 2021年10月日

1. 英文转中文的关键词查询

   

2. 待定

# 2021年10月6日

1. 灵感，感悟

   逻辑存储与物理存储之间的映射关系就像是key：value键值对之间的存储！！

   

2. 总结

   程序逻辑重于代码实现！！！（借用敏捷宣言思想：不是右边不重要，而是左边更为重要==》

   代码实现落地很重要，但在代码实现之前，需要有较为完整、清晰的程序逻辑。）

   就

   就

   就 

   Python零基础（极客Wilson）：Python基础语法、面向对象编程、判断循环、还有一些第三方库==》能够写出一些常用的小工具，和自己的一些应用程序==》如果想要深入研究学习，可以关注flask，janggo，tensorflow等框架，通过这些框架可以写出令自己满意的web程序和机器学习的程序==》感谢参与，希望大家可以写出令自己满意的Python程序

3. Python第三方库

   dbdb库：

4. 练习指南

   1.  Python爬取网页图片url
   2.  使用爬取的url下载图片
   3.  使用多线程的方式，同步下载多页图片

5. 英文转中文的关键词查询

   irls
   sea
   born
   iris
   deprecated
   norm
   kwarg
   Virginia
   hue
   raw

   url
   retrieve

6. 待定

# 2021年10月5日

1. Python外部库的使用

   numpy库：array(), zeros(), ones(), empty(), arange(), nan, 

   pandas库：其中2个重要的数据结构Series（一维）, DataFrame（二维）; DataFrame().T, reindex(), Series().dropna()

   seaborn库：

   warnings库：

   tensorflow库：机器学习相关

   iris库：与训练和测试数据相关

   

   网络库==》

   数据收集

   urllib库：request模块，parse模块（处理post数据的）

   requests库：

   格式处理

   BeautifulSoup库：pip3 install bs4

   lxml库：

   socket套接字库：

2. 人工智能之机器学习算法的通用处理步骤

   数据采集（调查问卷，网络数据等收集）；清洗；预处理（单位统一，格式调整；删减缺失值，异常值，得到优质数据等等）；建模（）；测试

3. 练习

   pip3 install numpy：安装numpy库

4. 零碎知识点

   Linux中，对文件标识的解读

   "-"：表示是一个文件，not a directory

   "d"：表示directory目录

   "l"：表示link链接

   哈希运算hash使用了哈希算法，会使得被运算值变成唯一的遗传字符

   列表可变，因而不能被进行哈希计算（unhashable）

   

   以下代码的执行与否和该代码所在的py文件是否被直接执行相关，如果直接执行，则进入if语句，如果被作为模块载入，则不被执行

   ![image-20211005211731509](NotesOfPython.assets/image-20211005211731509.png)

   （？模块运行？）

5. 在CentOS7上安装卸载python3与pip3（python3.6.4为例）

   【安装】

   （python3与pip3之间的关系：pip3 是 Python3 的包管理器。这意味着它是一个工具，允许你安装和管理不属于标准库的其他库和依赖。而pip3是python3安装路径中的bin文件夹下的一个可执行文件（，而不是文件夹directory））

   安装教程参考网址：https://www.cnblogs.com/shaosks/p/9172606.html

   关键步骤解释：

   ```shell
   # 做软链接
   　　　　ln -s /usr/local/python3/bin/python3.6 /usr/bin/python3　　
   # 设置pip软连接
   　　　　ln -s /usr/local/python3/bin/pip3.6 /usr/bin/pip3
   ###################　
   # 使用pip3下载的python库的默认存放路径
   /usr/local/python3/lib/python3.6/site-packages
   ```

   【卸载】

   参考网址：https://blog.csdn.net/u012551524/article/details/105137154/

   ```shell
   # 卸载python3（pip3会同时被卸载，并切pip3的软链接会失效；
   # （只是软链接不会自动被删除，需要手动删除））
         rpm -qa|grep python3|xargs rpm -ev --allmatches --nodeps       # 卸载pyhton3
         whereis python3 |xargs rm -frv           # 删除所有残余文件
         # 成功卸载！
         whereis python       # 查看现有安装的python
   ```

   

6. 英文转中文的关键词查询

   transaction
   transact
   transact
   prototype
   sonar
   redistribution
   strip
   decode
   encode
   array
   number
   prefix
   union

   optimize imports
   slice
   series
   tuple
   data
   frame
   pop
   capital

   sub
   delta
   random
   rand int
   path
   library
   resolve a thing
   credits
   utility
   scatter

   axis
   how
   mat
   plot
   lib
   un
   stack
   series
   series
   models
   module
   pre made
   estimator
   accuracy

   

7. 待定

# 2021年10月4日

1.  注意

   继承和多态都是面向对象非常重要的特征！

   type(a2)与isinstance(a2, Monster分别可以判断对象或者变量的类型与a2相关类是否是Monster类的子类

   Python中的多线程会使用消息队列进行线程同步？（我没太搞清楚queue.task_done()这个语句的含义）

   正则表达式：*（元字符，前面的字符出现0~多次，

   如a*，表示a出现0~多次）、

   ?（前面的字符出现0或1次，如）、

   .（任意单个字符）、

   ^（什么字符开头）、

   &（什么字符结尾，如jpg$）、

   {}（表示前面的字符出现指定次数，如ca{4}t，指a出现4次；ca{4, 6}t，指a出现4~6次）、

   []（如，c[bcd]t，表示匹配cbt, cct, 或cdt）、

   |（表示或者，选择左边或者右边，一般与括号搭配使用，如(03|04)，选择03或者04）

   +（表示前面的内容可以出现多次）、

   \d（表示匹配内容是一串数字，相当于，[0-9]+）、

   \D（表示提取出非数字）、

   \z（表示匹配内容是a-z的字符串）、

   ()（表示分组，搭配group()一起使用）、

   ^$（表示这一行是空行）、

   .*?（表示不适用贪婪模式（即尽可能长地匹配），比如说匹配caaaat，贪婪模式

   ca*会匹配到caaaa（最后一个a），不适用贪婪模式只匹配到ca）

2. 英文转中文的关键词查询

   None
   null
   raise
   recursive
   exit
   strategy
   abbreviated
   cheat sheet
   concretecreator
   iterate
   yield
   reduce
   module
   matplotlib
   mode
   module
   zen
   explicit

3. 待定

# 2021年10月3日

1.  问题：

   看不太懂

   ![image-20211003194709500](NotesOfPython.assets/image-20211003194709500.png)

2. 待定

# 2021年9月29日

1. 08 零基础学习Python学习进度==》21_异常的检测和处理
2. 待定

# 2021年9月29日

1. 
2. 待定