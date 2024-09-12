MyBatis 逆向工程（MyBatis Reverse Engineering）
---
是指通过 MyBatis Generator（MBG）工具，根据数据库中的表结构自动生成 MyBatis 相关的代码和配置文件。这些生成的代码和配置文件包括：

Java 实体类（POJO）：对应数据库表的 Java 类。

Mapper 接口：包含 CRUD（增删改查）操作的方法。

Mapper XML 文件：包含 SQL 语句的 XML 配置文件。

逆向工程的作用
逆向工程的主要作用是减少手动编写代码的工作量，提高开发效率。通过自动生成代码，开发者可以专注于业务逻辑的实现，而不需要花费大量时间编写基础的数据库操作代码。

mybatis-generator-core 自动生成 
---

**步骤**
1.	引入 Maven 依赖
在 pom.xml 中引入 mybatis-generator-core 的依赖
```yml
<dependency>
    <groupId>org.mybatis.generator</groupId>
    <artifactId>mybatis-generator-core</artifactId>
</dependency>
....
<build>
    <plugins>
        ......
        <plugin>
            <groupId>org.mybatis.generator</groupId>
            <artifactId>mybatis-generator-maven-plugin</artifactId>
            <version>1.4.0</version>
            <configuration>
                <configurationFile>src/main/resources/generatorConfig.xml</configurationFile>
                <verbose>true</verbose>
                <overwrite>true</overwrite>
            </configuration>
            <dependencies>
                <dependency>
                    <groupId>mysql</groupId>
                    <artifactId>mysql-connector-java</artifactId>
                    <version>8.0.31</version>
                </dependency>
            </dependencies>
        </plugin>
    </plugins>
</build>
```
2.	创建 MyBatis Generator 配置文件 generatorConfig.xml（与applicaton.yml 同级）

  > 请参考 [generatorConfig.xml](generate_mybatis_config.md) 获取更多信息。

3.	执行 MyBatis Generator 或者 运行插件mybatis-generator插件。
使用命令行工具运行 MyBatis Generator，自动生成代码：这个命令会读取 generatorConfig.xml 文件，根据你配置的内容生成相应的 model、mapper 以及 xml 文件。
```bash
   mvn mybatis-generator:generate 
```
4.	在项目中使用生成的代码
   生成完成后，你可以在项目的指定目录中找到相应的 model 类、mapper 接口以及 mapper.xml 文件。然后在业务逻辑中使用 Mapper 进行数据库操作，例如：
```java
@Autowired
private YourMapper yourMapper;

public List<YourDomainObject> getAllObjects() {
    return yourMapper.selectAll();
}
 ```

