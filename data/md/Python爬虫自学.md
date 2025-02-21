# 基础爬虫的各种程序总结



## <u>*2021-2022-1Python课程期末项目简介*</u>

1. 爬取当当网书籍信息，并保存为csv文件
2. 可以选择性下载图片（多线程方式）
3. 将爬取的书籍信息以list表形式插入MySQL数据库
   1. 改进：将csv文件中的信息插入数据库
4. （将MySQL数据库中的信息获取出来，保存为csv文件）



# 2021年12月2日

## 1. Q&A

- Python操作MySQL数据库

  - ```python
    '''fetchone'''
    import pymysql
    #打开数据库连接
    conn=pymysql.connect('localhost','root','123456')
    conn.select_db('pythondb')
    #获取游标
    cur=conn.cursor()
    
    cur.execute("select * from user;")
    while 1:
        res=cur.fetchone()
        if res is None:
            #表示已经取完结果集
            break
        print (res)
    cur.close()
    conn.commit()
    conn.close()
    print('sql执行成功')
    ————————————————
    版权声明：本文为CSDN博主「小小小小人ksh」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
    原文链接：https://blog.csdn.net/kongsuhongbaby/article/details/84948205
    ```

  - ```Python
    '''插入多条数据'''
    import pymysql
    #打开数据库连接，不指定数据库
    conn=pymysql.connect('localhost','root','123456')
    conn.select_db('pythondb')
    #获取游标
    cur=conn.cursor()
    
    #另一种插入数据的方式，通过字符串传入值
    sql="insert into user values(%s,%s,%s)"
    insert=cur.executemany(sql,[(4,'wen',20),(5,'tom',10),(6,'test',30)])
    print ('批量插入返回受影响的行数：',insert)
    cur.close()
    conn.commit()
    conn.close()
    print('sql执行成功')
    
    ```

  - 

# 2021年11月30日

## 1. Q&A

## 2. SS(Self Summary)

- 期末爬虫项目功能
  - 保存当当网指定书籍页面的部分书籍信息到指定的MySQL数据库中
  - 使用MySQL指定表中的图片url字段进行图片下载（外加多线程进行图片下载加速）
  - 修改MySQL中指定表中的图片url字段的记录（比如：将www.baidu.com.1.jpg修改为www.localhost.1.jpg）

# 2021年11月29日

## 1. Q&A

- **python连接mysql数据库报错init() takes 1 positional argument but 5 were given**

  - 错误原因未明。把连接语句修改成如下就好了

    ```python
    # 需要指定参数名
    db=pymysql.connect(host=dbhost,user=dbuser,password=dbpass,database=dbname)
    ```

# 2021年11月21日

## 1. Q&A

## 2. Python的性能

- 下载共168M，共40张图片
  - 使用单线程[所有]图片的下载时间为：start_time - end_time = 565.0484662055969秒【使用多线程可以只使用75秒左右的时间！】
- 

# 2021年11月20日

## 1. Q&A

- **解决ModuleNotFoundError: No module named 'pip'问题**

  - ```cmd
    # Python学习遇到小问题：
    # ModuleNotFoundError: No module named ‘pip’
    今天想要装一下wxPython第三方库来写一下Python的GUI的时候发现cmd窗口下无法执行pip命令，想了想昨晚好像是pip命令行提示了我有新版本可以更新使用，更新之后也不成功，但昨晚没有怎么理会，以为没事，但今早起来一看发现pip命令都用不了了，出现了ModuleNotFoundError: No module named 'pip’这个错误。
    查询了网上之后发现，这个错误可以通过两行简单的cmd命令行语句进行改正修复。
    
    python -m ensurepip
    python -m pip install --upgrade pip
    
    ————————————————
    版权声明：本文为CSDN博主「海hong」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
    原文链接：https://blog.csdn.net/haihonga/article/details/100168691/
    ```

- Python安装BeautifulSoup第三方库

  - 

    ```cmd
    pip3 install bs4
    # 而不是使用pip3 install beautifulsoup
    # 不过使用pip3 install beautifulsoup4可能是可以的
    ```

  - class_与class

    ```python
    find_add('', class_='')与find_add('', class='')
    ```

    

  - 

## 2.  Python第三方库

- **lxml**

  - 

    ```cmd
    pip3 install lxml
    ```

  - 

# 2021年11月19日

## 1. Q&A

- 正则表达式区分之：' .* ', ' .*? ', ' .+? '（'+'等价于{1,}，表示出现至少一次）
  - **1. ‘.\*’**
    - `.` 表示匹配除换行符 \n 之外的任何单字符，`*`表示零次或多次。所以`.*`在一起就表示任意字符出现零次或多次。没有`?`表示贪婪模式。比如`a.*b`，它将会匹配最长的以a开始，以b结束的字符串。如果用它来搜索`aabab`的话，它会匹配整个字符串`aabab`。这被称为贪婪匹配。
  - **2. ‘.\*?’**
    - `?`跟在*或者+后边用时，表示懒惰模式。也称非贪婪模式。就是匹配尽可能少的字符。就意味着匹配任意数量的重复，但是在能使整个匹配成功的前提下使用最少的重复。
      `a.*?b`匹配最短的，以a开始，以b结束的字符串。如果把它应用于`aabab`的话，它会匹配`aab`（第一到第三个字符）和`ab`（第四到第五个字符）。
  - **3. ‘.+?’**
    - 同上，`?`跟在*或者+后边用时，表示懒惰模式。也称非贪婪模式。就意味着匹配任意数量的重复，但是在能使整个匹配成功的前提下使用最少的重复。
      `a.+?b`匹配最短的，以a开始，以b结束的字符串，但a和b中间至少要有一个字符。如果把它应用于`ababccaab`的话，它会匹配`abab`（第一到第四个字符）和`aab`（第七到第九个字符）。注意此时匹配结果不是`ab`,`ab`和`aab`。因为a和b中间至少要有一个字符。

## 2. 基础知识

- 正则表达式
  - **/s**：匹配空白的字符。utf8的情况下匹配到，换行符\n，制表符\t，空格，等等。

  - 方法re.sub()。

    - re是正则regex的表达式，sub是substitute表示替换

  - re.S。

    - 如果不使用re.S参数，则只在每一行内进行匹配，如果一行没有，就换下一行重新开始。

    - 而使用re.S参数以后，正则表达式会将这个字符串作为一个整体，在整体中进行匹配。

    - ```python
      import re
      a = """sdfkhellolsdlfsdfiooefo:
      877898989worldafdsf"""
      b = re.findall('hello(.*?)world',a)
      c = re.findall('hello(.*?)world',a,re.S)
      print ('b is ' , b)
      print ('c is ' , c)
       
       
      # 输出结果：
      # b is  []
      # c is  ['lsdlfsdfiooefo:\n877898989']
      ```

- Python导入自己写的模块

  - ```python
    # 从module文件夹中导入save_data.py模块
    from module import save_data
    ```

    ![image-20211118182530834](Java爬虫自学.assets/image-20211118182530834.png)

  - 

# 2021年11月17日

## 1. Q&A

- PyCharm导入BeautifulSoup相关模块失败

  - 依据PyCharm给出的相关提示进行操作
    - 我对给出的提示得到的信息是：导入BeautifulSoup4模块（等到BeautifulSoup4模块导入之后，我再改为BeautifulSoup模块就可以使用了）

- requests.exceptions.MissingSchema: Invalid URL '//img.ivsky.com/img/tupian/li/202104/26/deck-004.jpg': No schema supplied. Perhaps you meant http:////img.ivsky.com/img/tupian/li/202104/26/deck-004.jpg?

  ![image-20211116201944324](Java爬虫自学.assets/image-20211116201944324.png)

  ```java
  D:\d1-DATAS\PycharmProjects\PythonScripting202120221\venv\Scripts\python.exe D:/d1-DATAS/PycharmProjects/PythonScripting202120221/top.song.www/final_project/some_parsing_tests/requests_and_beautifulsoup.py
  //img.ivsky.com/img/tupian/li/202104/26/deck-004.jpg
  Traceback (most recent call last):
    File "D:\d1-DATAS\PycharmProjects\PythonScripting202120221\top.song.www\final_project\some_parsing_tests\requests_and_beautifulsoup.py", line 25, in <module>
      req = requests.get(src)
    File "D:\d1-DATAS\PycharmProjects\PythonScripting202120221\venv\lib\site-packages\requests\api.py", line 75, in get
      return request('get', url, params=params, **kwargs)
    File "D:\d1-DATAS\PycharmProjects\PythonScripting202120221\venv\lib\site-packages\requests\api.py", line 61, in request
      return session.request(method=method, url=url, **kwargs)
    File "D:\d1-DATAS\PycharmProjects\PythonScripting202120221\venv\lib\site-packages\requests\sessions.py", line 528, in request
      prep = self.prepare_request(req)
    File "D:\d1-DATAS\PycharmProjects\PythonScripting202120221\venv\lib\site-packages\requests\sessions.py", line 456, in prepare_request
      p.prepare(
    File "D:\d1-DATAS\PycharmProjects\PythonScripting202120221\venv\lib\site-packages\requests\models.py", line 316, in prepare
      self.prepare_url(url, params)
    File "D:\d1-DATAS\PycharmProjects\PythonScripting202120221\venv\lib\site-packages\requests\models.py", line 390, in prepare_url
      raise MissingSchema(error)
  requests.exceptions.MissingSchema: Invalid URL '//img.ivsky.com/img/tupian/li/202104/26/deck-004.jpg': No schema supplied. Perhaps you meant http:////img.ivsky.com/img/tupian/li/202104/26/deck-004.jpg?
  
  Process finished with exit code 1
  ```

  - 解决思路：你应该确认一下对方有没有反爬机制，接下来直接运行是因为response没有返回任何内容，正则表达式匹配不到和条件相同的返回一个空，list就会报错了

- 
