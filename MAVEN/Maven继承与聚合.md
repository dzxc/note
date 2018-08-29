# 继承
##### 继承为了消除重复，我们把很多相同的配置提取出来
例如：grouptId，version等
父工程设置为被继承
	
	<packaging>pom</packaging>

##### 子工程继承父工程
省略父工程中定义的坐标除访问名称中的所有设定，添加继承父工程

	<parent>
		<groupId>…</groupId>
		<artifactId>… </artifactId>
		<version>… </version>
		<relativePath>../父工程项目名</relativePath>
	</parent>


##### 父工程统一管理子工程依赖版本

	<dependencyManagement>	
		<dependencies>
			//添加公共依赖包
		</dependencies>
	</dependencyManagement>

子工程仅仅添加依赖包，无需添加版本，版本由父工程继承而来
为了进一步便于管理，将所有的版本管理设置在一起，设置为系统属性值
	
	<properties>
		<junit.version>4.9</junit.version>
		……
	</properties>
引用使用${junit.version}格式进行，只能在依赖范围设置


父工程统一管理子工程依赖关系
如果所有子工程都需要依赖某些包，父工程可以通过设置依赖，将依赖关系传递到子工程中

	<dependencies>
		//添加公共依赖包
	</dependencies>

---

# 聚合
如果我们想一次构建多个项目模块，那我们就需要对多个项目模块进行聚合
	
	<modules>
		<module>../子项目名称1</module>
		<module>../子项目名称2</module>
		 <module>../子项目名称3</module>
	</modules>

聚合与继承的关系
聚合主要为了快速构建项目
继承主要为了消除重复