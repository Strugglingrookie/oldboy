#文件系统
***
###程序说明：
    基于线程的FTP服务器
    1.在之前开发的FTP基础上，开发支持多并发的功能
    2.不能使用SocketServer模块，必须自己实现多线程
    3.必须用到队列Queue模块，实现线程池
    4.允许配置最大并发数，比如允许只有10个并发用户

###实现功能如下：
    用户加密认证
    允许同时多用户登录（用到并发编程的知识，选做）
    每个用户有自己的家目录，且只能访问自己的家目录
    对用户进行磁盘配额，每个用户的可用空间不同（选做）
    允许用户在ftp server上随意切换目录
    允许用户查看当前目录下的文件
    允许上传和下载文件，并保证文件的一致性
    文件传输过程中显示进度条

###程序运行：
    python ftp_server/main.py

###程序结构：
    ftp_server/
    ├── README.md #项目说明
    ├── main.py #启动目录，程序入口。
    │── bin # 执行文件 目录
    │   ├── start.py  #导入主程序并启动
    │── config #配置文件
    │   ├── settings.py #存放IP，端口，链接数，用户数据目录等
    │── core #主要程序逻辑 在这个目录里
    │   └── server.py #具体实现的方法见里面每个方法的注释
    │── data #存放用户数据目录
    │   └── config.ini #用户信息，账号，密码，家目录以及目录大小限制