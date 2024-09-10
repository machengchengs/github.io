mybatis-generator-core 自动生成 

> Model（实体类） 和 Mapper 接口 以及 Mapper XML 文件
---
	• Model: 对应数据库表的实体类。
	• Mapper Interface: 用于定义数据库操作的接口。
	• Mapper XML: 包含实际的 SQL 语句或动态 SQL 的 XML 文件。

**步骤**
1.	引入 Maven 依赖
在 pom.xml 中引入 mybatis-generator-core 的依赖
```yml
<dependency>
    <groupId>org.mybatis.generator</groupId>
    <artifactId>mybatis-generator-core</artifactId>
</dependency>
```
2.	创建 MyBatis Generator 配置文件 generatorConfig.xml（与applicaton.yml 同级）

  > 请参考 [generatorConfig.xml](generate_mybatis_config.md) 获取更多信息。

3.	执行 MyBatis Generator
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

