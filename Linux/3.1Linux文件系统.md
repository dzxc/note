# Linux文件系统

### 目录
Linux目录与Windows的结构不同，Linux系统基本遵循FSSTND标准，使根目录非常简洁，只包含最基本的文件。
  Linux中没有Windows那种磁盘分区方式呈现给用户，Linux整个文件系统都是通过文件目录来展示，通过树形结构管理，这个树形结构与Windows的目录形式基本一致，但两者不完全一样，本质的管理方式不同。
  Linux以文件的形式存放各种数据或对象，整个文件系统的起始为根目录，Root => “ / ”，根目录是文件绝对路径的起始，符号就是一个斜杠，如“/ect”，代表根目录下的etc文件夹。Windows的文件路径是由盘符起始，比如“C:\window”

### 根目录下各文件夹介绍
##### 根目录下的文件夹都是比较重要的，这文件夹大多需要Root用户才能访问
##### /etc目录
这个目录主要存放系统管理相关的配置文件
列举部分常见的配置文件，注意：/etc目录下每一个配置文件都很重要，不熟悉这些文件之前千万不要随便修改，特别是在生产环境中的服务器

| 文件 | 作用 |
| ---- | ---- |
|passwd|不要望文生义以为这个文件是存密码的文件，这事用户信息记录文件，记录了用户名，UID，GUI，工作目录等信息，|
|shadow|这个文件就是存放用户密码的加密后的密码都存放在这里|
|group|存储用户组相关信息的文件|
|gshadow|组密码信息文件|
|hosts|在本机定义IP地址和域名对应关系，相当于Windows的hosts文件|
|resolv.conf|设置linux本地的客户端DNS的配置文件|
|sysconfig/network|配置主机名的目录|
|sysconfig/network-scripts/ifcfg-eth0|CentOS7之前网卡配置文件名，CentOS7之后网卡标识名变为enp0s3之类|
|fstab|记录开机要挂载的文件系统的文件，可以设置开机自动挂载的分区|
|rc.local | 存放开机自启动程序命令的文件:(可以利用chkconfig进行管理,自开发的程序可以防止在此处,实现开机的自启动,linux开机时会把rc.local里的文件内容执行一遍)|
|inittab|设定系统启动的时候,把系统设置成什么样的运行级别以及加载对应级别的文件设置，如果设置为0，|
|init.d|存放系统或者服务器以system v模式启动的脚本,存放yum 或者rpm安装的软件的的命令的目录|
|profile|系统全局变量永久生效的配置文件，主要用变更的是系统用户默认的环境设置:PATH, umask, TERM Type|
|sudoers|可以执行使用sudo命令的配置文件(权限提升)|
|systemd/system/*.wants|CentOS7新增目录文件，系统启动时需要使用，系统基本初始化的配置|
|service|记录服务与对应端口，修改后需要重启才能生效|
|sysctl.conf|系统内核参数配置文件，优化系统参数时会用到，CentOS7开始，配置文件被转移到/usr/lib/sysctl.d，但原来的配置文件/etc/sysctl.conf仍然可以生效，还可覆盖/usr/lib/sysctl.d的配置信息|
|crontab|配置系统计划任务，Root才有权限调用，crontab指令是给普通用户执行计划任务|
|syslog.conf|系统日志输出文件，CentOS5位syslog.conf，CentOS6开始改为rsyslog.conf|

### initab启动级别
initab每个级别对应着一个指令文件，里面描述系统启动后要执行的相关任务和相关服务
如：init0 ：/etc/rc.d/rc0.d
0:停机
1：单用户形式，只root进行维护
2：多用户，不能使用net file system
3：完全多用户
5：图形化
4：安全模式
6：重启 
