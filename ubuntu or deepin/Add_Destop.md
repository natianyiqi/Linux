# 在Linux desktop或者dock中创建快捷方式
  ## 以pycharm为例，其他可参照执行
      cd /usr/share/applications
      sudo gedit pycharm.desktop
          [Desktop Entry]
          Type=Application
          Name=Pycharm
          Icon=/opt/pycharm-2020.1.2/bin/pycharm.png
          Exec=sh /opt/pycharm-2020.1.2/bin/pycharm.sh
# 详解
## 概念
    Desktop Entry 文件是 Linux 桌面系统中用于描述程序启动配置信息的文件，它以 .desktop 为后缀名，相当于微软 Windows 系统下的桌面快捷方式。通常一个二进制可执行程序是一个没有后缀没有图标的文件，不可以随意移动。如果没有 desktop 文件，用户每次都需要打开一层层文件夹最后找到这个可执行文件，然后启动应用。这样打开应用的方式没有问题，但特别繁琐，而且可执行文件分布散乱，不易于管理。

    因此很多 Linux 发行版（包括 Deepin ) 都提供了启动器，便于集中管理应用程序。启动器本质是一个位于 /usr/share/applications/ 路径下的目录。启动器目录中存放着很多 .desktop 文件，每个 .desktop 文件都是一个应用程序的入口，并且 .desktop 文件可以显示图标，对用户更加友好。

## desktop文件模板  
    一个 desktop 文件主要由两部分组成，头部 [Desktop Entry] 声明（用于指定这是一个desktop文件）和一系列的参数/值对组成。一个 desktop 文件至少要指定 3 个参数的值（Name、Type 和 Exec）。
    demo1.desktop：

    [Desktop Entry]
    Name=<应用程序名>
    Type=Application
    Exec=<应用程序完整路径>
      
      1.Name: desktop 文件最终显示的名称（一定要注意和 desktop 文件名的区别）。
      2.Type: 用于指定 desktop 文件的类型（包括 3 种类型：Application、Link、Directory)。
      3.Exec: 用于指定二进制可执行程序的完整路径。

    大多数情况下，我们还需要指定 Icon 的值（一个 desktop 文件没有图标那也是缺少了点东西）

      1.Icon: 指定应用程序图标的完整路径(可以省略后缀名)。
      2.图标支持 png 格式、svg 格式等，图标的推荐尺寸为 128x128。
    因此一个基本的 desktop 文件模板应该像下面这样：

    demo2.desktop：
    [Desktop Entry]
    Name=<应用程序名>
    Type=Application
    Exec=<应用程序完整路径>
    Icon=<应用程序图标的完整路径>
## Categories 参数
    desktop 支持的参数远远不止上诉4个，在 deepin 系统还有一个比较常用的参数就是 Categories。
    Categories: 用于指定应用的分类（如果缺省则分类到其他应用）。
    我们打开启动器并切换到分类视图，可以看到刚刚添加到 CLion 被分类到其他应用了，但是我们想让他分到分类里面。
    解析Deepin Linux系统中的Desktop文件，附实例讲解
    deepin 启动器将所有应用分为10类，分别是网络应用、社交沟通、音乐欣赏、视频播放、图形图像、办公学习、阅读翻译、编程开发、系统管理和其他应用：
    解析Deepin Linux系统中的Desktop文件，附实例讲解
    下面我们修改 clion.desktop 文件，使 deepin 启动器能够正确地将 CLion 分类为编程开发：
    sudo gedit /usr/share/applications/clion.desktop
    在最后一行增加 Categories=Development 并保存：
    解析Deepin Linux系统中的Desktop文件，附实例讲解
    再打开启动器，可以发现 CLion 已经被正确地分类为编程开发分类下：
    解析Deepin Linux系统中的Desktop文件，附实例讲解

 

## 附表：Categories 对照表
    | Categories | 分类 | 
    | ------ | ------ | 
    | network | 网络应用 | 
    | Chat | 社交沟通 | 
    | Audio | 音乐欣赏 | 
    | Video | 视频播放 | 
    | Graphics | 图形图像 | 
    | Office | 办公学习 | 
    | Translation | 阅读翻译 | 
    | Development | 编程开发 | 
    | Utility | 系统管理 | 

