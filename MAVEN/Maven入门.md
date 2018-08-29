# Maven

##### Maven是跨平台的项目管理工具。
主要服务于基于Java平台的项目构建，依赖管理和项目信息管理。

#### Maven安装与配置

1. 检查jdk安装的情况(要1.6版本或以上):
Echo %JAVA_HOME%
Java -version
2. 到Maven官网下载对应Maven工具 ，链接 https://maven.apache.org/
3. 对apache-maven进行解压缩(解压目录最好不要有中文字)
4. 设置系统环境变量，MAVEN_HOME
5. 设置环境变量Path，将%MAVEN_HOME%\bin加入Path中，一定要注意要用分号；与其他值隔开
6. 验证安装是否成功，打开cmd窗口，敲入mvn –v 查看

#### Maven安装目录分析

bin：含有mvn运行的脚本
boot：含有plexus-classworlds类加载器框架
conf：含有settings.xml配置文件
lib：含有Maven运行时所需要的java类库
LICENSE.txt, NOTICE.txt, README.txt针对Maven版本，第三方软件等简要介绍

#### 配置信息

初始配置

1. 设置MAVEN_HOME环境变量
升级时只需要下载最新版本，解压缩后重新设置MAVEN_HOME环境变量即可

2. 设置MAVEN_OPTS环境变量
-Xms128m -Xmx512m

3. 配置用户范围的settings.xml
MAVEN_HOME/conf/settings.xml 全局的
~/.m2/settings.xml 

4. 默认仓库：当前用户路径C:\Users\[UserName]\.m2
localRepository：用户仓库，用于检索依赖包路径

用户Maven依赖包路径层次目录
