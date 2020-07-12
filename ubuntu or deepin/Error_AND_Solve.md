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
                 
