@Component
---
在 Spring 框架中，@Component 注解用于将一个类标记为 Spring 容器管理的组件。这意味着 Spring 会自动扫描带有 @Component 注解的类，并将其实例化为 Spring 管理的 Bean。
这样，就可以在其他地方通过依赖注入（Dependency Injection）来使用这些 Bean。

**为什么要使用 @Component 注解？**
- 自动扫描和实例化：

     当你在类上使用 @Component 注解时，Spring 会在应用启动时自动扫描并实例化这个类。这样你就不需要手动创建对象，Spring 会帮你管理对象的生命周期。

- 依赖注入：

     通过将类标记为 @Component，你可以使用 @Autowired 注解在其他类中注入这个 Bean。这使得代码更加简洁和易于维护。

- 统一管理：

     Spring 容器统一管理所有的 Bean，这使得可以更容易地进行配置、管理和扩展。
