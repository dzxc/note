# Maven

##### Maven是跨平台的项目管理工具。
主要服务于基于Java平台的项目构建，依赖管理和项目信息管理。利用pom.xml文件自动构建项目



### Maven的核心概念 

1. **坐标**
2. **依赖管理**
3. **仓库管理**
4. **生命周期**
5. **插件和目标**
6. **聚合继承**

#### Maven安装与配置

1. 检查jdk安装的情况(要1.6版本或以上):
Echo %JAVA_HOME%
Java -version
2. 到Maven官网下载对应Maven工具 ，链接 https://maven.apache.org/
3. 对apache-maven进行解压缩(解压目录最好不要有中文字)
4. 设置系统环境变量，MAVEN_HOME
5. 设置环境变量Path，将%MAVEN_HOME%\bin加入Path中，一定要注意要用分号；与其他值隔开
6. 验证安装是否成功，打开cmd窗口，敲入mvn –v 查看

#### Maven安装目录
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


### Maven仓库
用来统一存储所有Maven共享构建的位置就是仓库
##### Maven仓库布局
根据Maven坐标定义每个构建在仓库中唯一存储路径
大致为：groupId/artifactId/version/artifactId-version.packaging
仓库的分类
本地仓库
~/.m2/repository/
每个用户只有一个本地仓库
远程仓库
中央仓库：Maven默认的远程仓库，不包含版权资源
http://repo1.maven.org/maven2
私服：是一种特殊的远程仓库，它是架设在局域网内的仓库

Maven本地仓库文件有两个：
1. Maven依赖包目录repository
2. setting.xml
    settings.xml文件必须与maven安装路径下的内容保持一致
    配置中设置路径指向仓库目录
    <localRepository>D:\maven\repository</localRepository>
注意：
用户级别的仓库在全局配置中一旦设置，全局配置将不再生效，转用用户所设置的仓库，否则使用默认路径仓库

### Maven约定
使用Maven工具构建项目需要遵从Maven约定
项目目录下的应有的文件目录
    src/main/java —— 存放项目的.java文件
    src/main/resources —— 存放项目资源文件，如spring, hibernate配置文件
    src/test/java —— 存放所有测试.java文件，如JUnit测试类
    src/test/resources —— 测试资源文件
    target —— 项目输出位置
    pom.xml——maven项目核心配置文件

### Maven使用
新建项目
导入Maven项目
执行mvn命令



## 1. 坐标
是确定依赖包的具体的标识
Maven世界拥有大量构建，我们需要找一个用来唯一标识一个构建的统一规范
拥有了统一规范，就可以把查找工作交给机器

Maven坐标主要组成
groupId：定义当前Maven项目隶属项目，通常由公司域名倒写
artifactId：定义实际项目中的一个模块，项目名
version：定义当前项目的当前版本
packaging：定义该项目的打包方式

#### 2. 依赖管理

**依赖范围 scope **
其中依赖范围scope 用来控制依赖和编译，测试，运行的classpath的关系. 主要的是三种依赖关系如下：
1. compile： **默认编译依赖范围**。对于编译，测试，运行三种classpath都有效
2. test：测试依赖范围。只对于测试classpath有效
3. provided：已提供依赖范围。对于编译，测试的classpath都有效，但对于运行无效。因为由容器已经提供，例如servlet-api
4. runtime:运行时提供。例如:jdbc驱动

依赖管理
1. 传递性依赖
依赖本身具有传递性，如果 A.jar 依赖另 B.jar包，则一个项目中依赖A.jar后必然会依赖B.jar
受作用域影响，不同作用于之间的依赖传递表现不同
![](/MAVEN/images/3.png)

2. 可选依赖
可选依赖表示某些情况下被依赖项目可以指定自己所依赖的项目不被上层发现
是否向下传递
    <optional> 
        true/false
    </optional>  

3. 排除依赖
排除依赖，上层可以指定不包含某些某些

    <exclusions>
    	<exclusion>
    		所包含坐标
    	<exclusion>
    </exclusions>

排除依赖包中所包含的依赖关系
不需要添加版本，直接类别排除

4. 依赖冲突

如果直接与间接依赖中包含有同一个坐标不同版本的资源依赖，以直接依赖的版本为准（就近原则）
如果直接依赖中包含有同一个坐标不同版本的资源依赖，以配置顺序下方的版本为准（就近原则）

http://mvnrepository.com/


### 插件目标
Maven的核心仅仅定义了抽象的生命周期，具体的任务都是交由插件完成的
每个插件都能实现多个功能，每个功能就是一个插件目标
Maven的生命周期与插件目标相互绑定，以完成某个具体的构建任务
例如compile就是插件maven-compiler-plugin的一个插件目标

<build>
	<plugins>
		<plugin>
     	 		<groupId>org.apache.maven.plugins</groupId>
			<artifactId>maven-source-plugin</artifactId>
      		<version>2.2.1</version>
      		<executions>
            			<execution>
					<goals>
						<goal>jar-no-fork</goal>
            				</goals>
            				<phase>verify</phase>
				</execution>
    			</executions>
  		</plugin>
	</plugins>
</build>