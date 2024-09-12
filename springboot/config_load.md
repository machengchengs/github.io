# Spring Boot 加载自动配置文件的方式总结

Spring Boot 提供了多种机制来加载自定义配置文件。本文将介绍4种主要方式及其优缺点、适用场景，并给出最佳实践和对比。

## 对比表
| 特性/方式                        | `spring.config.import`                              | 多环境配置 (`application-{profile}.yml`)              | `@ConfigurationProperties`                         | `@PropertySource`                                 |
|-----------------------------------|-----------------------------------------------------|-------------------------------------------------------|---------------------------------------------------|---------------------------------------------------|
| **支持文件类型**                 | `.yml`, `.properties`, 云服务等                      | `.yml`, `.properties`                                 | `.yml`, `.properties`                             | 仅 `.properties`                                  |
| **动态加载**                     | 支持                                                 | 不支持                                                | 不支持                                            | 不支持                                            |
| **适合的配置内容**               | 模块化配置、动态配置                                 | 不同环境下的配置                                      | 大型复杂配置                                      | 简单 `.properties` 配置                          |
| **使用场景**                     | 从多个不同来源加载配置，适合模块化和复杂的动态配置场景 | 在开发、测试、生产环境下加载不同的配置                | 适合复杂的、嵌套的配置结构                        | 加载外部 `.properties` 文件，适合简单配置场景    | 
| **优点**                         | 灵活性高，支持多个来源                               | 简单易用，适合环境切换                                | 类型安全，支持复杂配置                            | 轻量，灵活加载简单 `.properties` 文件            |
| **缺点**                         | 配置复杂，无法嵌套 `spring.config.import`            | 不适合动态配置                                        | 不能动态加载，配置文件更改需要重启应用             | 不支持复杂结构  | 需要在启动时指定，不能动态更改                   |

## 最佳实践建议
- 推荐使用 spring.config.import：适用于复杂的模块化、动态配置场景，尤其是当配置文件来源复杂、需要灵活性时。
- 使用多环境配置：当项目需要根据环境（开发、测试、生产）来区分配置时，使用 application-{profile}.yml 是最方便和推荐的方式。
- 使用 @ConfigurationProperties：如果需要类型安全、复杂的配置结构，@ConfigurationProperties 是首选，可以有效管理复杂的嵌套配置。
- 使用 @PropertySource：适合加载少量外部 .properties 文件，适用于小型应用或简单配置场景。

## 1. spring.config.import 
**详细说明**
spring.config.import 属性允许你在 application.yml 或 application.properties 文件中指定要导入的配置文件。Spring Boot 会自动加载这些配置文件。
**示例**
```yml
spring:
  config:
    import: "file:./config/*.properties"
```
多个文件配置
```yml
# application.yml
spring:
  config:
    import: optional:classpath:/custom-config.yml, optional:file:/etc/myapp/config.yml
```
优点：

- 简单易用，无需编写额外的配置类。

- 支持通配符，可以一次性导入多个配置文件。

- 可以在 application.yml 或 application.properties 文件中统一管理配置文件的导入。

缺点：

 - 仅适用于 Spring Boot 2.4 及以上版本。

 - 不支持动态加载配置文件。
**适用范围**
适用于需要一次性导入多个配置文件的场景，特别是当这些配置文件不区分环境时。

## 利用 Spring Boot 多环境配置加载机制
**详细说明**
Spring Boot 支持多环境配置，你可以通过 application-{profile}.properties 或 application-{profile}.yml 文件来定义特定环境的配置。Spring Boot 会根据激活的配置文件加载相应的配置文件。

**示例**
```yml
spring:
  profiles:
    active: customer
```
优点：

- 支持多环境配置，可以根据不同的环境加载不同的配置文件。

- 配置文件命名规范，易于管理。

缺点：

- 需要为每个环境创建单独的配置文件，可能会导致配置文件数量较多。

- 不支持动态加载配置文件。

**适用范围**
适用于需要根据不同环境加载不同配置文件的场景，如开发、测试、生产环境。

## 3. 使用 @ConfigurationProperties
**详细说明**
@ConfigurationProperties 注解可以将配置文件中的属性绑定到一个 Java 对象上。
**示例**
```bash
# application.yml
myapp:
  feature:
    enabled: true
    name: "My Custom Feature"

```java
@Component
@ConfigurationProperties(prefix = "myapp.feature")
public class FeatureConfig {
    private boolean enabled;
    private String name;
    // Getters and setters
}
```
优点:
  - 类型安全：将配置项映射到 Java 类，具有类型安全性，编译时即可发现配置问题。
	- 支持复杂结构：非常适合嵌套结构的配置，如对象、集合、Map 等。
	- 易于测试：配置项可以通过依赖注入轻松测试。

缺点:
 - 不能动态导入配置：无法在运行时动态加载配置，只能通过重启应用更新配置。

**适用场景**
- 适用于需要类型安全、复杂嵌套配置结构的场景，尤其是**大型应用程序中**的数据库、缓存、API 配置等。

## 4. @PropertySource
**详细说明**
@PropertySource 用于加载特定的 .properties 文件，将其注入到 Spring 环境中，通常与 @Value 或 Environment 结合使用。
**示例**
```bash
# custom-config.properties
myapp.feature.enabled=true
myapp.feature.name=My Custom Feature

```java
@Configuration
@PropertySource("classpath:/custom-config.properties")
public class CustomConfig {

    @Value("${myapp.feature.enabled}")
    private boolean enabled;

    @Value("${myapp.feature.name}")
    private String name;
    
    // Getters and setters
}
```
优点
	- 灵活加载：可以从类路径或文件系统中加载任意 .properties 文件，甚至是外部文件。
	- 轻量：简单轻量，适合用于加载少量配置项。

缺点
  - 只支持 .properties：不支持 .yml 文件。
	- 不支持复杂结构：不能自动将配置映射为复杂对象，通常需要手动使用 @Value 来获取值。
    

**使用场景**
	- 适用于需要加载简单的外部 .properties 文件，且文件内容较少的场景。



