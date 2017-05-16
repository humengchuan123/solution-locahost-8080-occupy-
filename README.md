# solution-locahost-8080-occupy-
 Whenever you want to use port 8080 is occupied very trouble, This here .could you view and quickly solve port 8080 occupied yes method
Window 通过cmd查看端口占用、相应进程、杀死进程等的命令
     一、 查看所有进程占用的端口 
在开始-运行-cmd,输入执行命令：netstat –ano可以查看所有进程 

-a 显示所有连接和监听端口

-n 以数字形式显示地址和端口号。 此选项一般与 -a选项组合使用

-o 显示与每个连接相关的所属进程 ID。


for exameple:
Active Connections

Proto Local Address          Foreign Address        State           PID

TCP    0.0.0.0:8080           0.0.0.0:0              LISTENING       656

TCP    0.0.0.0:8080           0.0.0.0:0              LISTENING       656

可见，占用8080端口的进程的PID是656


   二、查看占用指定端口的程序 
当你在用tomcat发布程序时，经常会遇到端口被占用的情况，我们想知道是哪个程序或进程占用了端口，可以用该命令 netstat –ano|findstr “指定端口号” 二、查看占用指定端口的程序 当你在用tomcat发布程序时，经常会遇到端口被占用的情况，我们想知道是哪个程序或进程占用了端口，可以用该命令 netstat –ano|findstr “指定端口号” 二、查看占用指定端口的程序 
当你在用tomcat发布程序时，经常会遇到端口被占用的情况，我们想知道是哪个程序或进程占用了端口，可以用该命令 netstat –ano|findstr “指定端口号” 
如:查询占用了8080端口的进程：netstat -ano|findstr "8080"

三、执行命令：tasklist

图像名                       PID 会话名           会话#       内存使用

========================= ====== ================ ======== ============

TNSLSNR.exe                  656 Console                 0      8,992 K
可见，该占用8080端口的进程是TNSLSNR.exe
方法一：
然后通过任务管理器，终止进程TNSLSNR.exe
当然也有其他办法：
方法二：使用命令杀死进程
1>首先找到进程号对应的进程名称
tasklist|findstr 进程号
如:tasklist|findstr 3112

2>然后根据进程名称杀死进程
taskkill /f /t /im 进程名称
如:taskkill /f /t /im /javaw.exe
