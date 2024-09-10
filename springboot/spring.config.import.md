# spring.config.import 的5中方式

在 Spring Boot 2.4 及以上版本中，spring.config.import 是用于导入额外的配置文件或配置源的一种机制
以下是 spring.config.import 支持的几种模式及其具体含义

| 选项        | 示例配置内容                               | 说明                                                   | 真实目录示例                                                          |
|-------------|--------------------------------------------|--------------------------------------------------------|----------------------------------------------------------------------|
| `classpath` | `classpath:/config/application-extra.yml`  | 从项目类路径中加载配置文件，通常位于 `src/main/resources` | `[项目根目录]/src/main/resources/config/application-extra.yml`        |
| `file`      | `file:/external/config.yml`                | 从文件系统中的绝对路径加载配置文件                       | `/external/config.yml`（Linux/Unix）或 `C:/external/config.yml`（Windows） |
| `configserver` | `configserver:http://configserver.local:8888` | 从远程配置服务器加载配置文件                              | 由配置服务器决定，如 `http://configserver.local:8888`                 |
| `configtree` | `configtree:/etc/app/config`              | 从文件系统中的目录加载配置文件，通常用于容器或 Kubernetes 环境 | `/etc/app/config`                                                    |
| `optional`  | `optional:file:/external/config.yml`       | 可选加载配置文件，如果文件不存在，应用仍可继续启动       | `/external/config.yml`（Linux/Unix）或 `C:/external/config.yml`（Windows） |
