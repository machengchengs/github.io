YML 常用语法
---
> YAML是一种数据序列化语言，旨在方便用户使用，并能与现代编程语言很好地配合使用，以完成常见的日常任务
>
> 例如，缩进可用于结构，冒号用于分隔 键/值对，破折号用于创建“项目符号”列表。
>
[跳转至YML长文示例链接](https://yaml.org/spec/1.2.2/#25-full-length-example)

## 以下是一些 YAML 语法的基本示例
### 1. 基本数据类型
```yml
# 字符串
string: "Hello, World!"

# 数字
integer: 42
float: 3.14

# 布尔值
boolean: true

# 空值
null_value: null
```
### 2. 列表
```yml
# 列表
fruits:
  - apple
  - banana
  - orange

# 嵌套列表
nested_list:
 - [姓名，小时，平均值] 
 - [马克·麦奎尔，65，0.278] 
 - [萨米·索萨，63，0.288]
```
### hash 映射
```yml
# 映射
person:
  name: John
  age: 30
  city: New York

# 嵌套映射
address:
  street: 123 Main St
  city: New York
  state: NY
  zip: 10001
```
