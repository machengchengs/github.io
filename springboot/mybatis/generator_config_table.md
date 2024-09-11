generatorConfig.xml 之《table》
---
翻译：

> https://mybatis.org/generator/configreference/table.html

### `<table>` 元素

`<table>` 元素用于配置 MyBatis Generator 如何生成代码和配置文件。每个 `<table>` 元素对应数据库中的一个表。

#### 属性

- **`tableName`** (必填):
  - 数据库表的名称。可以使用 SQL 通配符（如 `%`）来匹配多个表。
  - 示例：`tableName="user"`

- **`schema`** (可选):
  - 数据库模式（Schema）的名称。如果未指定，MyBatis Generator 将使用默认模式。
  - 示例：`schema="public"`

- **`catalog`** (可选):
  - 数据库目录（Catalog）的名称。如果未指定，MyBatis Generator 将使用默认目录。
  - 示例：`catalog="my_catalog"`

- **`domainObjectName`** (可选):
  - 生成的 Java 实体类的名称。如果未指定，MyBatis Generator 将根据表名自动生成类名。
  - 示例：`domainObjectName="User"`

- **`mapperName`** (可选):
  - 生成的 Mapper 接口的名称。如果未指定，MyBatis Generator 将根据表名自动生成接口名。
  - 示例：`mapperName="UserMapper"`

- **`sqlMapName`** (可选):
  - 生成的 SQL Map 文件的名称。如果未指定，MyBatis Generator 将根据表名自动生成文件名。
  - 示例：`sqlMapName="UserMapper.xml"`

- **`enableInsert`** (可选):
  - 是否生成插入方法。默认值为 `true`。
  - 示例：`enableInsert="true"`

- **`enableSelectByPrimaryKey`** (可选):
  - 是否生成根据主键查询的方法。默认值为 `true`。
  - 示例：`enableSelectByPrimaryKey="true"`

- **`enableSelectByExample`** (可选):
  - 是否生成根据示例查询的方法。默认值为 `true`。
  - 示例：`enableSelectByExample="true"`

- **`enableUpdateByPrimaryKey`** (可选):
  - 是否生成根据主键更新的方法。默认值为 `true`。
  - 示例：`enableUpdateByPrimaryKey="true"`

- **`enableDeleteByPrimaryKey`** (可选):
  - 是否生成根据主键删除的方法。默认值为 `true`。
  - 示例：`enableDeleteByPrimaryKey="true"`

- **`enableDeleteByExample`** (可选):
  - 是否生成根据示例删除的方法。默认值为 `true`。
  - 示例：`enableDeleteByExample="true"`

- **`enableCountByExample`** (可选):
  - 是否生成根据示例统计记录数的方法。默认值为 `true`。
  - 示例：`enableCountByExample="true"`

- **`enableUpdateByExample`** (可选):
  - 是否生成根据示例更新的方法。默认值为 `true`。
  - 示例：`enableUpdateByExample="true"`

- **`selectByPrimaryKeyQueryId`** (可选):
  - 用于指定根据主键查询的 SQL 语句的 ID。
  - 示例：`selectByPrimaryKeyQueryId="selectUserById"`

- **`selectByExampleQueryId`** (可选):
  - 用于指定根据示例查询的 SQL 语句的 ID。
  - 示例：`selectByExampleQueryId="selectUsersByExample"`

- **`modelType`** (可选):
  - 生成的 Java 实体类的类型。可选值为 `conditional`、`flat` 和 `hierarchical`。默认值为 `conditional`。
  - 示例：`modelType="flat"`

- **`escapeWildcards`** (可选):
  - 是否对 SQL 通配符进行转义。默认值为 `false`。
  - 示例：`escapeWildcards="true"`

- **`delimitIdentifiers`** (可选):
  - 是否对标识符进行分隔。默认值为 `false`。
  - 示例：`delimitIdentifiers="true"`

- **`delimitAllColumns`** (可选):
  - 是否对所有列名进行分隔。默认值为 `false`。
  - 示例：`delimitAllColumns="true"`

#### 子元素

- **`generatedKey`**:
  - 用于配置自动生成的主键。
  - 示例：
    ```xml
    <generatedKey column="id" sqlStatement="MySql" identity="true"/>
    ```

- **`columnOverride`**:
  - 用于覆盖列的默认配置。
  - 示例：
    ```xml
    <columnOverride column="username" property="userName"/>
    ```

- **`ignoreColumn`**:
  - 用于忽略某些列。
  - 示例：
    ```xml
    <ignoreColumn column="password"/>
    ```

### 示例配置

以下是一个完整的 `<table>` 元素配置示例：

```xml
<table tableName="user" domainObjectName="User" mapperName="UserMapper" sqlMapName="UserMapper.xml" modelType="flat">
    <generatedKey column="id" sqlStatement="MySql" identity="true"/>
    <columnOverride column="username" property="userName"/>
    <ignoreColumn column="password"/>
</table>
