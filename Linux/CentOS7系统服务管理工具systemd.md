# systemd
CentOS7开始的一个比较重要的改变就是使用systemd管理机制，负责初始化系统和管理系统与服务，

### 在系统初始化上，
sysvinit：在systemd之前使用的sysvinit，串行启动比较费时。通过在/etc/inittab 中定义好的默认“runlevel（运行级别）”来加载对应的运行级别指令
systemd 则是采用target（运行目标）的新方式来启动，里面的目标类似inittab重定义的运行级别相似，如“multi-user.target” 对应着 init3级别，引入systemd后，原来的sysvinit的inittab就被取代，

### 服务管理上
sysvinit：提供service chkconfig命令管理服务
systemd：提供systemctl管理服务
sysvinit 和 systemd指令对比

|sysvinit|systemd|功能|
|----|----|----|
|service xxx start| systemctl start xxx.service|启动某个服务|
|service xxx stop | systemctl stop  xxx.service|关闭某个服务|
|service xxx restart | systemctl restart  xxx.service|重启某个服务|
|service xxx reload | systemctl reload  xxx.service|从新载入某个服务配置信息而不中断服务|
|service xxx status | systemctl status  xxx.service|查看服务运行状态|
|chkconfig xxx on | systemctl enable  xxx.service|设置某个服务开机自启|
|chkconfig xxx off | systemctl disable  xxx.service|禁止某个服务开机自启|
|chkconfig xxx  | systemctl is-enable  xxx.service|查看某个服务当前环境下是启用还是禁用|
|chkconfig --list | systemctl list-unit-files --type=service|输出各个运行级别下所有服务的启用和禁用情况|
|chkconfig xxx --list | ls /etx/systemd/system/*.wants/xxx.service |查看各个运行级别下某个服务的启用和禁用情况|
|chkconfig xxx --add | systemctl daemon-reload |创建一个新的服务文件或者变更配置时使用|

### systemd系统电源管理

|指令|功能|
|----|----|
|systemd poweroff|关闭系统|
|systemd reboot|重启系统|
|systemd suspend|进入待机模式|
|systemd hibernate|进入休眠模式|
|systemd hy-bird-sleep|进入混合休眠模式|