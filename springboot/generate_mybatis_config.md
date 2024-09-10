MyBatis Generator 
---
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
        PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">

<!-- 参考信息： https://mybatis.org/generator/configreference/xmlconfig.html -->
<generatorConfiguration>
    <!-- 数据库连接配置， 项目使用的maven管理就不再需要配置驱动的jar包所在位置了 -->
    <!-- <classPathEntry location="path/to/jdbc/driver.jar" />-->

    <context id="tribeDB" targetRuntime="MyBatis3">
        <!-- 数据库连接信息 -->
        <jdbcConnection driverClass="com.mysql.cj.jdbc.Driver"
                        connectionURL="jdbc:mysql://localhost:3306/tribe_development"
                        userId="root"
                        password="12345678">
            <!--MySql 无法正确支持 SQL 目录和架构: 参考目录： https://mybatis.org/generator/usage/mysql.html-->
            <!-- 配置这个属性可以避免生成生成 MySql 数据库默认的一些表信息-->
            <property name="nullCatalogMeansCurrent" value="true" />
        </jdbcConnection>

        <!-- javaTypeResolver: Java 类型解析器 -->
        <!-- javaTypeResolver 作用是将数据库中的数据类型映射为 Java 类型 -->
        <javaTypeResolver>
            <!--对数据库中 DECIMAL 和 NUMERIC 列不使用 java.math.BigDecimal 类型：-->
            <property name="forceBigDecimals" value="false" />
        </javaTypeResolver>

        <!-- javaModelGenerator: 会构建与自检表匹配的主键类、记录类和按示例查询类 -->
        <!-- targetPackage: 这是放置生成的类的包, MyBatis Generator 将根据需要为生成的包创建文件夹 -->
        <!-- targetProject: 用于指定生成的对象的目标项目, 指定将保存对象的项目和源文件夹-->
        <javaModelGenerator targetPackage="com.tribe.store.model" targetProject="src/main/java">
            <!--属性“enableSubPackages”控制实际包的计算方式。
              如果为true，则计算的包将是targetPackage加上表的目录和模式(如果存在)的子包。
              如果为false(默认值)，则计算的包将与targetPackage属性中指定的完全相同-->
            <property name="enableSubPackages" value="true" />
            <!--
                当为true时，MyBatis Generator将插入代码来修剪字符字段。可以用<table>或<columnOverride>元素中的trimStrings属性重写。
                默认值为false
            -->
            <property name="trimStrings" value="true" />
        </javaModelGenerator>

        <!-- sqlMapGenerator 元素用于定义 SQL 映射生成器的属性。 -->
        <!-- sqlMapGenerator 作用为每个表构建一个 MyBatis 格式的 SQL 映射 XML 文件。 -->
        <!-- targetPackage: 这是放置生成的 SQL Map 的包 -->
        <!-- targetProject: 用于为生成的 SQL 映射指定目标项目-->
        <sqlMapGenerator targetPackage="com.tribe.store.mapper" targetProject="src/main/resources">
            <!--
             假设数据库myschema有一个表 MYTABLE。还假设 targetPackage 属性设置为“com.mycompany”。
             如果此属性为 true，则为该表生成的 SQL Map 将放置在包“com.mycompany.myschema”中。
             如果此属性为 false，则生成的 SQL Map 将放置在“com.mycompany”模式中。
             默认值为 false。
            -->
            <property name="enableSubPackages" value="true" />
        </sqlMapGenerator>

        <!-- javaClientGenerator 元素用于生成的 Java 接口，以便轻松使用生成的 Java 模型和 XML 映射文件 -->
        <javaClientGenerator type="XMLMAPPER" targetPackage="com.tribe.store.mapper" targetProject="src/main/java">
            <property name="enableSubPackages" value="true" />
        </javaClientGenerator>

        <!-- 表配置 -->
        <table tableName="%"/>
    </context>
</generatorConfiguration>
```
