@Autowired 
---

### @Autowired 注解
@Autowired 是一个用于依赖注入的注解。它的主要作用是：

- 自动装配：

     通过 @Autowired 注解，Spring 会自动将匹配的 Bean 注入到目标字段、构造函数或方法参数中。

- 字段注入：

     你可以在类的字段上使用 @Autowired 注解，Spring 会自动将匹配的 Bean 注入到该字段中。

- 构造函数注入：

     你可以在类的构造函数上使用 @Autowired 注解，Spring 会自动将匹配的 Bean 作为构造函数的参数注入。

- 方法注入：

     你可以在类的方法上使用 @Autowired 注解，Spring 会自动将匹配的 Bean 作为方法的参数注入。

### 总结


- @Autowired 注解用于字段、构造函数或方法，表示 Spring 应该自动注入依赖。

- @Autowired 用于自动装配依赖，使得 Spring 可以将匹配的 Bean 注入到目标字段、构造函数或方法参数中。
