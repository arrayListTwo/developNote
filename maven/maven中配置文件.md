* Settings.xml文件
```xml
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <localRepository/> <!-- 指定本地仓库位置 -->
  <interactiveMode/> <!-- 指定 maven 的运行模式是否为交互模式 -->
  <usePluginRegistry/> <!-- 目前少用，指定插件配置文件 -->
  <offline/> <!-- 指定是否为离线模式，在不需要网络交互的时候使用 -->
  <pluginGroups/> <!-- 指定插件所在的路径，maven 将通过该路径查找插件 -->
  <servers/> <!-- 指定服务器的用户名、密码等，用于上传，下载文件等 -->
  <mirrors/> <!-- 指定 maven 主仓库的镜像 -->
  <proxies/> <!-- 网络代理配置，用于有代理的网络 -->
  <profiles/> <!-- pom.xml 中的 profile 能够用于公共配置的部分 -->
  <activeProfiles/>
</settings>
```
* maven管理中的项目中pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <!-- 指定了当前pom的版本 -->
  <modelVersion>4.0.0</modelVersion>

  <!-- 项目基本设置 -->
  <groupId>...</groupId> <!-- 项目所在组、机构名称<-项目名> -->
  <artifactId>...</artifactId> <!-- 项目产品名称<-模块名> -->
  <!-- 第一个0表示大版本号
		第二个0表示分支版本号
		第三个0表示小版本号
		0.0.1
		snapshot 快照
		alpha 内部测试
		beta 公测
		Release 稳定
		GA 正式发布 -->
  <version>...</version> <!-- 项目产品版本 -->
  <packaging>...</packaging> <!-- 项目包类型，打包类型，默认为jar包，可被打包成war zip pom -->

  <!-- 项目依赖包 -->
  <dependencies>
	<!-- 可有多个dependency子标签 -->
  	<dependency>
		<groupId><groupId>
		<artifactId></artifactId>
		<version></version>
		<type></type>
		<!-- 依赖范围 ，
			maven中提供了三种classpath：
				1、编译 
				2、测试
				3、运行
			值为compile：（默认），编译、测试、运行都有效
			值为provided：在编译和测试时有效，在运行时无效
			值为runtime：在测试和运行时有效，在编译时无效
			值为test：在测试时有效，则此依赖只能在test中使用，在主代码中使用则报错
			值为import：导入的范围，它之使用在dependencyManagement中，表示从其它的pom中导入dependency的配置
			 -->
		<scope><scope> 

		<optional></optional> <!-- true | false，设置依赖是否可选，默认为false。false代表可继承，true代表显式引入 -->
		<!-- 排除依赖传递列表 -->
		<exclusions>
			<exclusion>
			<exclusion>
		</exclusions> 

	</dependency>
  </dependencies> 

  <parent>...</parent> <!-- 项目所继承的父项目 -->

  <!-- 继承父系的依赖  依赖的管理 -->
  <dependencyManagement>
  	<dependencies>
		<dependency>
		</dependency>
	</dependencies>
  </dependencyManagement> 

  <!-- 所包含的子模块，聚合 --> 
  <modules>
  	<module>
	</module>
  </modules> 

  <properties>...</properties> <!-- 定义变量 -->

  <!-- 项目构建设置 -->
  <build>
	<!-- 插件列表 -->
	<plugins>
		<plugin>
			<groupId><groupId>
			<artifactId></artifactId>
			<version></version>
		</plugin>
	<plugins>
  </build>

  <!-- 项目报告生成设置 -->
  <reporting>...</reporting>

  <!-- 项目更多设置 -->
  <name>...</name> <!-- 项目名称(项目描述名) -->
  <description>...</description> <!-- 项目描述 -->
  <url>...</url> <!-- 项目网站(项目地址) -->
  <inceptionYear>...</inceptionYear> <!-- 项目起始年份 -->
  <licenses>...</licenses> <!-- 项目许可 -->
  <organization>...</organization> <!-- 项目组织 -->
  <developers>...</developers> <!-- 项目开发人员 -->
  <contributors>...</contributors> <!-- 项目贡献者 -->

  <!-- 环境设置 -->
  <issueManagement>...</issueManagement> <!-- 问题管理 -->
  <ciManagement>...</ciManagement>
  <mailingLists>...</mailingLists>
  <scm>...</scm> <!-- 代码管理 -->
  <prerequisites>...</prerequisites>
  <repositories>...</repositories> <!-- 指定依赖包所在的仓库 -->
  <pluginRepositories>...</pluginRepositories> <!-- 指定插件所在的仓库 -->
  <distributionManagement>...</distributionManagement> <!-- 指定发布位置 -->
  <profiles>...</profiles> <!-- 针对不同的环境使用不同的配置，如开发与生产环境的数据库是不同的 -->
</project>
```