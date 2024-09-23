## Spring @Bean 和 @Component 注解

1. @Bean

	•	定义方式：通常在配置类（使用 @Configuration 注解的类）中使用。
	•	用途：用于显式地声明一个 bean，通常用于从第三方库或无法使用注解的类创建 bean。
```java
@Configuration
public class AppConfig {
    @Bean
    public MyService myService() {
        return new MyService();
    }
}
```

2.  @Component

	•	定义方式：可以直接在类上使用，Spring 会自动扫描指定包下的类并注册为 bean。
	•	用途：用于标记一个类为 Spring 的组件，通常用于自定义的服务、控制器、仓储等类。
	•	示例：
```java
@Component
public class MyService {
    // business logic
}
```
## 使用场景：
- @Bean 适合需要更多配置或者来自第三方库的 bean。
- @Component 适合于 Spring 自己管理的组件，通常是业务逻辑相关的类。
