# 在Linux desktop或者dock中创建快捷方式
  ## 以pycharm为例，其他可参照执行
      cd /usr/share/applications
      sudo gedit pycharm.desktop
          [Desktop Entry]
          Version=1.0
          Type=Application
          Name=Pycharm
          Icon=/opt/pycharm-2020.1.2/bin/pycharm.png
          Exec=sh /opt/pycharm-2020.1.2/bin/pycharm.sh
          MimeType=application/x-py;
          Name[en_US]=pycharm
