## 2021年9月12日

一、

1. 网络配置目录：

   cd /etc/sysconfig/network-scripts

2. 查看文件命令

   cat, tac, head（eg. head -n 20）, tail,

   nl 带行号显示

   more 按页显示文件内容（空格翻页，Enter向下翻一行）

   less 同more，并且可以往前翻页

3. 查看命令使用文档：

   man [命令]

4. 命令模式：

   /set	向下查找set关键词（n（next），向下查找下一个；Shift+n或大写N，向上查找下一个）

   ?set	向上查找set关键词

5. 待定

二、

1. 硬链接与软连接

   创建链接：ln 命令

   ​	创建文件：touch f1 （虽然没有指定文件后缀，但f1它确实是一个文件）

   ​	创建一个硬链接：ln f1 f2（f2是f1的硬链接）

   ​					软连接：ln -s f1 f3（f3是f1的软连接，并且f3是类似与Windows快捷方式的文件类型，并不算真正意义上的可读文件）

   ![image-20210912092728821](Linux-basics.assets/image-20210912092728821.png)

   定向信息到指定文件中：echo "信息" >> 指定的文件名

   ![image-20210912093008699](Linux-basics.assets/image-20210912093008699.png)

   软链接会随着源文件被删除而失效

   ![image-20210912093725096](Linux-basics.assets/image-20210912093725096.png)

   

2. 待定

三、Linux账号管理（Centos7为例）

1. 用户

   添加==》

   useradd -选项 用户名

   -m：自动出啊年这个用户的主目录

   -G：给用户分配组。

   eg. useradd -m butterfly-c7

   ![image-20210912100118034](Linux-basics.assets/image-20210912100118034.png)

   本质：Linux中一切皆文件，这里的添加用户实际上是向某一个文件中写入了相关信息！/etc/passwd

   ![image-20210912123052339](Linux-basics.assets/image-20210912123052339.png)

   用户密码保存位置：/etc/shadow（保存的都是经过自动加密处理的密码）

   删除用户==》（这里，c7代表Centos7）

   userdel -r butterfly-c7：删除用户butterfly-c7并清除相关文件

   修改用户==》

   usermod -d /home/233 butterfly-c7：只是向/etc/passwd中添加了相关信息，如果233文件夹不存在，不会自动创建233文件夹！

   切换用户==》

   su butterfly-c7

   退出当前用户：exit

   hostname：查看当前主机名

   ![image-20210912101353406](Linux-basics.assets/image-20210912101353406.png)

   hostname butterfly-valley：将当前主机名修改为butterfly-valley（如果使用的shell进行连接，重新连接之后即可生效）

   用户的密码配置==》

   passwd butterfly-c7（root用户 配置指定用户密码）

   passwd（配置当前用户密码）

   锁定账户＝＝》

   passwd -l butterfly-c7：锁定之后该用户butterfly-c7就不能登录 了

   passwd -d butterfly-c7：清空该用户密码，并且即使使用空密码也不能登录

2. 待定

   

四、用户组管理

1. 用户组

   创建一个用户组==》

   groupadd 用户组名：groupadd butterflysworld

   cat /etc/group

   用户组是有id号的，可以指定，如果不指定就自增

   group -g 520 butterflysworld2

   ![image-20210912103805637](Linux-basics.assets/image-20210912103805637.png)

   删除用户组==》

   groupdel butterflysworld2

   修改用户组的权限信息和名字==》

   groupmod -g 666 -n new-butterflysworld butterflysworld

   ![image-20210912122654002](Linux-basics.assets/image-20210912122654002.png)

   

2. 待定

五、磁盘管理

1. df，dt

   df：列出文件系统整体的磁盘使用量（参数-h，大小用M的形式显示）

   du：检查磁盘控件使用量（-a，显示所有all，包括隐藏文件）

   ​	du -sm /*（查看根目录/下各个文件夹的大小）

2. mount

   挂载：mount

   ![image-20210912124308252](Linux-basics.assets/image-20210912124308252.png)

   卸载： umount -f [挂载位置] 强制卸载

3. 待定

六、Linux进程管理

1. 命令

   ```bash
   ps -aux|grep mysql	#查看（mysql相关的）所有进程
   ps -ef	#可以查看到父进程的信息（并不明显）
   ps -pu	#进程树
   	-p	显示父进程id
   	-u	显示用户组
   ```

   结束进程：

   kill -9 [进程id]（强制结束）

2. 待定

七、rpm安装jdk上线项目

1. 下载、安装环境

   ![image-20210912171014696](Linux-basics.assets/image-20210912171014696.png)

   Centos7环境变量路径：/etc/profile

   配置Java的jdk环境变量

   ![image-20210912171402031](Linux-basics.assets/image-20210912171402031.png)

   防火墙端口查看与开启

   查看防火墙开启端口：firewall -cmd --list-ports

   开启防火墙指定端口：firewall -cmd --zone=public --add-port=9000/tcp --permanet

   操作防火墙之后需要重启防火墙：systemctl restart firewalld.service

   ![image-20210912172520160](Linux-basics.assets/image-20210912172520160.png)

   ![image-20210912173216494](Linux-basics.assets/image-20210912173216494.png)

2. Tomcat安装

   解压文件apache-tomcat-9.0.22.tar.gz

   ![image-20210912172835167](Linux-basics.assets/image-20210912172835167.png)

   ![image-20210912172910332](Linux-basics.assets/image-20210912172910332.png)

   ![image-20210912173031602](Linux-basics.assets/image-20210912173031602.png)

   

3. yum安装Docker

   ![image-20210912173944517](Linux-basics.assets/image-20210912173944517.png)

   

4. Vmware网络配置（Centos7）

   动态配置文件

   ![image-20210912175015135](Linux-basics.assets/image-20210912175015135.png)

   静态配置文件

   ![image-20210912175410888](Linux-basics.assets/image-20210912175410888.png)

   图形化界面配置：nm-connection-editor（唤出图形界面进行相关配置）

5. 其它

   查看Linux版本信息：cat /etc/redhat-release 

八、