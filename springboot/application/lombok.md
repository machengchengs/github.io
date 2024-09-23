## 使用 Lombok 自动生成 getter 和 setter 的步骤
在 Spring Boot 中，自动生成 getter 和 setter 方法的功能通常是通过使用 Lombok 库来实现的。

Lombok 提供了简单的注解，可以减少样板代码（如 getter、setter、toString、equals 等），并且可以集成到 IDE（如 IntelliJ IDEA 或 Eclipse）中，方便开发时使用。

## 1.添加 Lombok 依赖
```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.30</version> <!-- 确保使用最新版本 -->
    <scope>provided</scope>
</dependency>
```

## 2. 安装 Lombok 插件（IDEA 或 Eclipse）
### 插件的作用
> 尽管 Lombok 的注解在编译时已经有效，
>
> 但没有插件支持，IDE 无法识别这些编译时生成的代码，导致开发体验下降，甚至可能显示无关的错误提示。
>
> 安装 Lombok 插件后，IDE 能够准确处理这些注解，使代码提示、自动补全、错误检查等功能正常工作，从而显著提升开发效率和体验。


## 3. 使用 Lombok 注解生成 getter 和 setter
在实体类中使用 Lombok 提供的注解，如 @Getter、@Setter 来自动生成 getter 和 setter 方法：
```java
import lombok.Getter;
import lombok.Setter;
import java.util.Date;

@Getter
@Setter
public class Product {
    private Long id;
    private String title;
    private Date publishedAt;
}
```
这将自动生成 id、title 和 publishedAt 的 getter 和 setter 方法。

## 4. 其他 Lombok 注解

除了 @Getter 和 @Setter，Lombok 还提供了其他有用的注解：

- @Data: 生成 getter、setter、toString、equals 和 hashCode 方法，常用于实体类。
- @NoArgsConstructor: 生成无参构造方法。
- @AllArgsConstructor: 生成包含所有字段的构造方法。
- @Builder: 生成 builder 模式的类。
