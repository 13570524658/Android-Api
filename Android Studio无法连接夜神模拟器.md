#  Android Studio无法连接夜神模拟器

    解决方法：

    1）进入CMD，转到夜神安装目录

    2）执行命令：nox_adb.exe connect 127.0.0.1:62001，连接到服务器。

    例如：

    夜神安装目录是D:\Program Files\Nox\bin

    在命令行中输入cd D:\Program Files\Nox\bin  回车

    输入D: 回车，

    输入执行命令nox_adb.exe connect 127.0.0.1:62001，回车。

    这个时候查看Android Studio，就可以看到已经连接上了夜神模拟器。
