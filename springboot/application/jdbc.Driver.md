`com.mysql.jdbc.Driver` 和 `com.mysql.cj.jdbc.Driver` 的区别与选择原则
---

> com.mysql.jdbc.Driver 和 com.mysql.cj.jdbc.Driver 是 MySQL 数据库的 JDBC 驱动类，分别适用于不同的 MySQL 版本和 MySQL Connector/J 版本。
>
> 如果你使用的是 MySQL 8.x 或更高版本，建议选择 com.mysql.cj.jdbc.Driver。



| 特性               | `com.mysql.jdbc.Driver`            | `com.mysql.cj.jdbc.Driver`          |
|--------------------|-------------------------------------|-------------------------------------|
| **版本**           | MySQL Connector/J 5.x               | MySQL Connector/J 6.x 及更高版本    |
| **支持的 MySQL 版本** | MySQL 5.x 及更早版本            | MySQL 8.x 及更高版本                |
| **特性**           | 支持 MySQL 5.x 及更早版本           | 支持 MySQL 8.x 及更高版本，提供更多特性和改进 |
| **兼容性**         | 与旧版本的 MySQL 数据库兼容         | 与 MySQL 8.x 及更高版本兼容         |
| **推荐使用**       | 如果你使用的是 MySQL 5.x 或更早版本 | 如果你使用的是 MySQL 8.x 或更高版本 |

## 选择原则

1. **MySQL 版本**：
   - 如果你使用的是 MySQL 5.x 或更早版本，选择 `com.mysql.jdbc.Driver`。
   - 如果你使用的是 MySQL 8.x 或更高版本，选择 `com.mysql.cj.jdbc.Driver`。

2. **依赖版本**：
   - 如果你使用的是 MySQL Connector/J 5.x 版本，选择 `com.mysql.jdbc.Driver`。
   - 如果你使用的是 MySQL Connector/J 6.x 或更高版本，选择 `com.mysql.cj.jdbc.Driver`。

## 示例

假设你使用的是 MySQL 8.x 版本，你应该选择 `com.mysql.cj.jdbc.Driver`：

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/mydb
    username: root
    password: secret
    driver-class-name: com.mysql.cj.jdbc.Driver
```
