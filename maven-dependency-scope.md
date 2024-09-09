# maven scope
在 Maven 中，<scope> 标签用于指定依赖的范围（Scope），即依赖在构建过程中的使用场景。Maven 提供了以下几种 scope 值：
- compile
- provided
- runtime
- test
- system
- import

### Maven 生命周期阶段

Maven 的生命周期由一系列的阶段组成，每个阶段执行特定的任务。以下是 Maven 的主要生命周期阶段：

1. **validate**：验证项目是否正确，所有必要信息是否可用。
2. **compile**：编译项目的源代码。
3. **test**：使用合适的单元测试框架测试编译后的源代码。
4. **package**：将编译后的代码打包成可分发的格式（如 JAR、WAR）。
5. **verify**：运行任何检查以验证包是否有效并符合质量标准。
6. **install**：将包安装到本地仓库，供本地其他项目使用。
7. **deploy**：将最终的包复制到远程仓库，供其他开发者和项目使用。

### 依赖范围（Scope）与生命周期阶段

以下是每个 `scope` 值对应的生命周期阶段汇总：

| Scope     | 编译时 | 测试时 | 运行时 |
|-----------|--------|--------|--------|
| `compile` | ✔️     | ✔️     | ✔️     |
| `provided`| ✔️     | ✔️     | ❌     |
| `runtime` | ❌     | ✔️     | ✔️     |
| `test`    | ❌     | ✔️     | ❌     |
| `system`  | ✔️     | ✔️     | ❌     |
| `import`  | ❌     | ❌     | ❌     |

