## mybatis-spring-boot-starter 的作用
- 自动配置
自动配置数据源：根据 application.properties 或 application.yml 文件中的配置，自动配置数据库连接池。
- 自动扫描 Mapper 接口
自动扫描 Mapper 接口：通过 @MapperScan 注解或 @Mapper 注解，自动扫描并注册 MyBatis 的 Mapper 接口。

- 简化配置
简化配置过程：减少了手动配置的工作量，只需要配置数据库连接信息，Spring Boot 会自动完成其他配置。

- 支持多种数据库
支持多种数据库：根据配置的数据库连接信息，支持多种数据库，如 MySQL、PostgreSQL、Oracle 等。


##  mybatis-generator-core 的作用

- 自动生成实体类：根据数据库表结构生成 Java 实体类。

- 自动生成 Mapper 接口：生成 MyBatis 的 Mapper 接口，定义数据库操作方法。

- 自动生成 Mapper XML 文件：生成 MyBatis 的 XML 映射文件，定义 SQL 语句和结果映射。

## mysql-connector-java 的作用
- mysql-connector-java 是 MySQL 数据库的 JDBC 驱动，用于连接 MySQL 数据库。它提供了与 MySQL 数据库进行交互的 API。

## 总结
- mybatis-generator-core：用于生成 MyBatis 代码，但不包含数据库驱动。

- mysql-connector-java：用于连接 MySQL 数据库，提供数据库驱动。
- mybatis-spring-boot-starter：简化 MyBatis 与 Spring Boot 的集成，自动配置数据源、事务管理，并自动扫描和注册 Mapper 接口。

