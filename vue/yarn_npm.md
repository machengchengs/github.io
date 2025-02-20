## yarn 和 yarn install 

yarn 和 yarn install 两个命令的作用基本相同，都是用来安装项目的依赖的，但有一些细微的区别。

### yarn install
- 作用：yarn install 是最常用的命令，用来根据 package.json 中的依赖列表安装所有的依赖包。
- 执行时：它会读取项目根目录中的 package.json 文件，然后安装其中列出的所有依赖。如果你已经有 yarn.lock 文件，yarn install 还会确保依赖版本与你的 yarn.lock 中定义的版本保持一致。
- 可以带选项：比如 --production，用来只安装生产依赖，跳过开发依赖。

### yarn
- 作用：yarn 本质上是 yarn install 的快捷方式。它可以省略 install，因为 yarn 默认会执行 install 命令。
- 执行时：与 yarn install 相同，它会根据 package.json 安装所有的依赖。
- 简洁性：只需要执行 yarn，它会自动执行 yarn install。

### 结论
- yarn 和 yarn install 功能上是重复的，二者等效。
- yarn 更简洁，适合在终端中快速运行。
- 在实际使用中，很多开发者习惯使用 yarn，而不专门写 install，因为它的语法更短。

## yarn  和 npm 安装依赖包
在项目中 不推荐 混用它们，因为它们在包管理和锁定依赖的方式上存在一些差异，可能会导致依赖管理上的问题。
### 混用的潜在问题：
- 1.	依赖版本管理不同：
  - npm 和 yarn 都有自己的锁文件：npm 使用 package-lock.json，yarn 使用 yarn.lock。它们的工作方式不同，可能会导致依赖版本不一致的问题。
  -	如果你在项目中使用 npm 安装了依赖并生成了 package-lock.json，然后用 yarn 安装依赖，它会基于 yarn.lock 生成新的锁文件，可能与 npm 安装的版本不一致。
- 2.	包的安装顺序不同：
	- yarn 和 npm 在处理依赖安装时的细节有所不同，yarn 会更并行化地处理依赖，而 npm 可能会更序列化。混用它们时可能会导致一些意想不到的行为。
-	3.	工作区支持：
	- yarn 支持工作区（workspaces），而 npm 在较早版本中并不支持，尽管从 npm 7 开始也加入了工作区支持。如果项目中混用它们，可能会导致一些兼容性问题。
-	4.	不同的命令：
	- yarn 和 npm 有些命令是不同的。例如，npm run 对应的是 yarn 的 yarn，但它们的一些标志和用法有所不同。如果你混用它们，可能会导致命令的混淆和错误。

### 推荐做法
	•	选择一个包管理器：建议选择 npm 或 yarn 中的一个进行包管理，并坚持使用它。这有助于避免潜在的依赖冲突和其他问题。
	•	如果选择 yarn，使用 yarn install 安装依赖，并确保在项目中只有 yarn.lock 文件。
	•	如果选择 npm，使用 npm install 安装依赖，并确保在项目中只有 package-lock.json 文件。
