# The Error in using Deepin and Give a Solution.
## Curl Error
       Error1 :  Failed to connect to 127.0.0.1 port 8888
       Solve1 :  lsof -i:8888     #查看端口是否被占用，如果被占用可清理或其他操作。
                 env| grep -i proxy       #查看代理
                 https_proxy=127.0.0.1:8888
                 http_proxy=127.0.0.1:8888
                 socks_proxy=
                 ftp_proxy=
                 # 经查看，原因是127.0.0.1:8888被当做代理占用了，需要关闭。
                 # 执行如下：
                 export http_proxy=''
                 export https_proxy=''
## Time Error
       Error1: The time difference between Windows and Deepin is 8 hours.
       Solve1: # in Deepin
               timedatectl set-local-rtc 1 --adjust-system-clock
       Solve2: # in Windows
               方法二：windows下
               在Windows下进行如下修改：
               徽标键+R 输入 regedit 回车
               路径：
               计算机\HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\TimeZoneInformation
               在右边窗口空白处右键 ===》新建一个  QWORD （64位值）
               名字叫 RealTimeIsUniversal 然后确认
               双击它将值改为 1 回车 其它不要操作
## Mysql Error
       Error1: mysql安装后没有密码。
       Solve1：首先确保mysql服务已经启动。启动命令： service mysql start
               然后直接无密码登录： mysql -uroot -p   然后弹出要输入密码的命令： 直接回车跳过。
               进入mysql。
               在mysql中执行如下命令。
               use mysql；
               update user set password=password('密码') where user='root';                  #如果此条命令报错，可以执行替换命令： 
               替换命令（无错不执行)
               update mysql.user set authentication_string=password('新密码') where user='root';        #如果此条命令报错，继续执行下一行替换命令：
               替换命令2（无错不执行）
               set password for 用户名@localhost = password('新密码');                    #如果三条都执行了还是报错，那么请看Solve2。
               执行完成后刷新权限：
               flush privileges;
               退出重新登录即可。
       Solve2: 同样需要先保证mysql服务已经启动。service mysql start
               执行如下命令： 
               mysqladmin -uroot password '密码'
               执行完成后直接登录即可。


