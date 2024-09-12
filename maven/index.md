## maven 官方网站
> https://maven.org.cn/
## 什么是maven
>  Maven 是意第绪语，意思是知识的积累者，现在可以用于构建和管理任何基于 Java 的项目的工具
## maven的特征
- 依赖管理
- 统一项目目录结构
- 自动化项目构建

### 依赖管理：
> 方便快捷的管理项目依赖的资源(jar包)，避免版本冲突问题

1. 在没有maven管理项目依赖时，需要引入大量的jar包、
2. jar包和jar包之间很多时候是需要版本匹配的，如果版本不匹配，此时很容易出现版本冲突问题

maven进行项目依赖(jar包)管理，可以很便捷的解决这个问题。 只需要在maven项目的pom.xml文件中填写好对应的配置就行
```java
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-dependencies</artifactId>
    <version>2.2.13.RELEASE</version>
    <type>pom</type>
    <scope>import</scope>
</dependency>
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.2.4</version>
</dependency>
<dependency>
    <groupId>com.github.pagehelper</groupId>
    <artifactId>pagehelper-spring-boot-starter</artifactId>
    <version>1.3.0</version>
</dependency>
<dependency>
    <groupId>com.github.oshi</groupId>
    <artifactId>oshi-core</artifactId
    <version>5.6.0</version>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```
### 统一项目结构 
目录说明： 
- src/main/java: java源代码目录 
- src/main/resources: 配置文件信息 
- src/test/java: 测试代码 
- src/test/resources: 测试配置文件信息

### 项目构建
> maven提供了自动化项目构建方式

当开发完成一套系统，代码需要进行编译、测试、打包、发布，这些操作如果需要反复进行就显得特别麻烦，而Maven提供了一套简单的命令来完成项目构建。

-  maven clean
-  maven compile
-  maven test
-  maven package
-  maven deploy
