@Component 和 @Autowired 
---

### @Component 注解
@Component 是一个用于将**类**标记为 Spring 组件的注解。它的主要作用是：

- 标记组件：

     将一个类标记为 Spring 管理的组件，使得 Spring 容器在启动时会自动扫描并实例化这个类。

- 自动扫描：

     当 Spring 应用启动时，它会扫描带有 @Component 注解的类，并将其实例化为 Spring 管理的 Bean。

- 依赖注入：

     通过将类标记为 @Component，你可以使用 @Autowired 注解在其他类中注入这个 Bean。

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

### 区别
**作用对象不同**：

- @Component 注解用于类，表示这个类是一个 Spring 管理的组件， 创建一个单例实例。

- @Autowired 注解用于字段、构造函数或方法，表示 Spring 应该自动注入依赖。

**功能不同**:

- @Component 用于标记类为 Spring 组件，使得 Spring 容器可以自动扫描并实例化这个类。

- @Autowired 用于自动装配依赖，使得 Spring 可以将匹配的 Bean 注入到目标字段、构造函数或方法参数中。
