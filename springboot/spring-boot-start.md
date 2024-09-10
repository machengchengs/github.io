# Spring Boot Starter Web 与 Spring Boot Starter Tomcat 的区别

在 Spring Boot 中，`spring-boot-starter-web` 和 `spring-boot-starter-tomcat` 是两个不同的模块，它们分别用于不同的场景和用途。
## 主要区别总结

| 特性               | Spring Boot Starter Web             | Spring Boot Starter Tomcat          |
|--------------------|-------------------------------------|-------------------------------------|
| **主要用途**       | 构建基于 Spring MVC 的 Web 应用程序和 RESTful API | 提供嵌入式 Tomcat 服务器           |
| **包含内容**       | Spring MVC, 嵌入式 Tomcat, JSON 支持, 视图解析 | 嵌入式 Tomcat                      |
| **适用场景**       | 构建 Web 应用程序和 RESTful API     | 需要使用嵌入式 Tomcat 服务器        |
| **依赖**           | `spring-boot-starter-web`           | `spring-boot-starter-tomcat`        |

## 选择建议
- **如果你需要构建基于 Spring MVC 的 Web 应用程序或 RESTful API**，选择 `spring-boot-starter-web`。它包含了构建 Web 应用程序所需的所有依赖，包括嵌入式 Tomcat 服务器。
- **如果你只需要嵌入式 Tomcat 服务器**，并且不需要 Spring MVC 或其他 Web 相关功能，可以选择 `spring-boot-starter-tomcat`。

## 1. Spring Boot Starter Web

### 用途
`spring-boot-starter-web` 是一个综合性的启动器，用于构建基于 Spring MVC 的 Web 应用程序。默认web服务器是tomcat， 如果不修改web服务器，可以不添加 Spring Boot Starter Tomcat

### 主要功能
- **Spring MVC**：提供 Spring MVC 框架，用于构建 Web 应用程序和 RESTful API。
- **嵌入式 Tomcat**：默认包含嵌入式 Tomcat 服务器，用于运行 Web 应用程序。
- **JSON 支持**：自动配置 Jackson，用于处理 JSON 数据。
- **视图解析**：支持多种视图技术（如 Thymeleaf、JSP、Freemarker）。

### 适用场景
- 构建基于 Spring MVC 的 Web 应用程序。
- 开发 RESTful API。
- 需要处理 HTTP 请求和响应的场景。

### 示例依赖
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

## 2. Spring Boot Starter Tomcat

### 用途
`spring-boot-starter-tomcat` 是一个独立的启动器，用于提供嵌入式 Tomcat 服务器。它通常与 spring-boot-starter-web 一起使用，但也可以单独使用

### 主要功能
- **嵌入式 Tomcat**：提供嵌入式 Tomcat 服务器，用于运行 Web 应用程序。

- **Servlet 容器**：支持 Servlet 3.1 规范。

### 适用场景
- 需要使用嵌入式 Tomcat 服务器运行 Web 应用程序。
- 在需要自定义 Tomcat 配置的场景中使用

### 示例依赖
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-tomcat</artifactId>
</dependency>
```
