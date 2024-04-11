- # yarn  快速入门笔记
  
  > 快速、可靠、安全的依赖管理工具: [yarn 中文官网](https://yarn.bootcss.com/)
  
  Yarn 是一个包管理器。它可以让你使用并分享 全世界开发者的（例如 JavaScript）代码。
  
  代码通过 **包（package）** (或者称为 **模块（module）**) 的方式来共享。 一个包里包含所有需要共享的代码，以及描述包信息的文件，称为 `package.json` 。
  
- # 安装

- ## Install via npm
  
  ```bash
  npm install --global yarn
  ```
  
- ## macOS
  
  ```bash
  brew install yarn
  ```
  
- ## 升级 yarn
  
  ```bash
  yarn --version
  brew upgrade yarn
  ```
  
- ## 设置环境变量
  
  ```bash
  which yarn
  
  export PATH="$PATH:/usr/local/bin"
  
  source ~/.bash_profile
  ```
  
- # 使用方法

- **初始化一个新项目**
  
  ```
  yarn init
  ```
  
- **添加依赖包**
  
  ```bash
  yarn add [package]
  yarn add [package]@[version]
  yarn add [package]@[tag]
  ```
  
- **将依赖项添加到不同依赖项类别中**
  
  分别添加到 `devDependencies`、`peerDependencies` 和 `optionalDependencies` 类别中：
  
  ```bash
  yarn add [package] --dev
  yarn add [package] --peer
  yarn add [package] --optional
  ```
  
- `yarn add [package] --dev`

  - 这个命令用于将一个包作为开发依赖（`devDependencies`）添加到你的项目中。开发依赖是那些只在开发过程中需要，但在生产环境下不必要的包。这包括像测试框架、构建工具等。
  - 例如，如果你想添加一个用于单元测试的库（如 Jest），你应该将它作为开发依赖添加，因为你不需要在生产环境中运行你的测试。

- `yarn add [package] --peer`

  - 使用这个命令将一个包添加为同级依赖（`peerDependencies`）。同级依赖通常用于插件或库的场景，当你的包需要使用宿主项目中已安装的包时使用。
  - 同级依赖不会被直接安装。相反，它们指定了你的包运行所需的依赖版本范围。这主要是为了避免依赖冲突，确保宿主项目中不会安装与插件或库不兼容的依赖版本。

- ##### `yarn add [package] --optional`

  - 此命令将一个包作为可选依赖（`optionalDependencies`）添加到项目中。可选依赖是指那些即使安装失败，也不会影响项目正常运行的包。它们对于一些只在特定条件下需要的功能非常有用。
  - 例如，某些功能可能仅在特定平台上可用，或者项目可以有选择地提供额外的功能，这时可以将相关包作为可选依赖安装。

- **升级依赖包**

  ```bash
  yarn upgrade [package]
  yarn upgrade [package]@[version]
  yarn upgrade [package]@[tag]
  ```

- **移除依赖包**

  ```bash
  yarn remove [package]
  ```

- **安装项目的全部依赖**

  ```bash
  yarn
  或者
  yarn install
  ```

- 全局安装

```bash
yarn global add package
```



- ## **npm 迁移到 yarn**

  > [从 npm 迁移到 yarn](https://yarn.bootcss.com/docs/migrating-from-npm/)

  `package.json` 配置文件,尝试运行 `yarn` 命令重新生成 `node_modules` 模块依赖.

  自动生成 `yarn.lock` 文件并纳入版本控制,确保其他人运行 `yarn` 命令的效果保持一致.

  从 `1.7.0` 版本后可以使用 `yarn import` 命令导入由 `npm` 生成 `package-lock.json` 文件依赖.

  其他人可以保持不变,不强制要求所有人同时从 `npm` 前移到 `yarn`.

  如果决定 `yarn` 不适合可以删除 `yarn.lock` 文件而继续使用原来的 `npm`.

  如果正在使用 `npm-shrinkwrap.json` 文件可能导致不同的依赖环境,所有人同时前移到 `yarn` 可能比较方便,只需要删除 `npm-shrinkwrap.json` 并自动生成 `yarn.lock` 文件.

- # npx

  `npx` 是一个 npm 包运行器，随 npm 5.2.0 及更高版本一同被引入。

  `npx` 让你能够运行包的最新版本而无需全局安装它们，同时还能运行在项目中声明的依赖包的命令。

- ### `npx` 的主要用途

  1. 直接运行包中的命令：即使没有全局安装一个包，也能执行它的命令。这对于运行最新版本的工具或尝试不想在系统上永久安装的包非常有用。
  2. 执行项目内部安装的包命令：允许你运行项目依赖中的命令，而不必通过复杂的脚本路径。
  3. 避免全局安装包：有些工具建议全局安装，但这可能会导致版本冲突或权限问题。使用 `npx` 可以避免这些问题，因为它总是运行最新版本或指定版本的命令。
  4. 运行 `npm` 包中的代码示例或初始化命令，而无需显式安装它们。例如，创建一个新的 React 应用程序。

  ```bash
  npx 包名 --参数
  ```
  -