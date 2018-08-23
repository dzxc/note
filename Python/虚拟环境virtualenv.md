# virtualenv

### 安装
	pip install virtualenv

基本使用

	创建虚拟环境：
	virtualenv [选项]<参数> #
	virtualenv -p /usr/bin/python3.5 test　　　　# 创建指定test文件夹，包含了Py库及相关工具，-p 指定具体Python解释器
	　　
	激活环境：
	source test/bin/activate　　　
	关闭环境：
	. test/bin/deactivate
	回到系统默认的PY环境
	
	删除虚拟环境
	rm -rf test

# virtualenvwrapper
管理虚拟环境工具，（非必须安装）
前提安装virtualenv库
安装virtualenvwrapper

	pip install virtualenvwrapper
	Windows ：pip install virtualenvwrapper-win　　
	
安装完成后，在~/.bashrc写入以下内容

	export WORKON_HOME=~/Envs
	source /usr/local/bin/virtualenvwrapper.sh　　
	#第一行：virtualenvwrapper存放虚拟环境目录
	#第二行：virtrualenvwrapper会安装到python的bin目录下，所以该路径是python安装目录下bin/virtualenvwrapper.sh
	source ~/.bashrc　　　　#读入配置文件，立即生效
　

---

# virtualenvwrapper基本使用

1.创建虚拟环境　mkvirtualenv

mkvirtualenv venv　　　
　　这样会在WORKON_HOME变量指定的目录下新建名为venv的虚拟环境。

　　若想指定python版本，可通过"--python"指定python解释器

	mkvirtualenv --python=/usr/local/python3.5.3/bin/python venv

2. 基本命令 　

	查看当前的虚拟环境目录
	workon
	
	切换到虚拟环境
	workon py3
	
	退出虚拟环境
	deactivate
	
	删除虚拟环境
	rmvirtualenv venv