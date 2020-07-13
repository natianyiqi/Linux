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
