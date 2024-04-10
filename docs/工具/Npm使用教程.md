# Npm 使用教程

##  常用命令

- `npm init` 初始化项目，其实就是创建一个 `package.json` 文件。
- `npm install` 安装所有项目依赖。
- `npm help xxx` 查看 `xxx` 命令的帮助信息。

### npm search 搜索（快捷方式：find, s）

- `xxx` 搜索 `xxx` 如：`npm search jquery`。

### npm install 安装 （快捷方式：i）

- `xxx` 搜索并安装 xxx（局部）。安装多个依赖可用空格分割，如 `npm i jquery bootstrap`。
- `xxx -g` 搜索并安装 xxx（全局）。安装多个同上。
- `xxx -D` 安装并将依赖信息写在 `package.json` 中的 `devDependencies` 中。
- 快捷方式 `i` 均可，如 `npm i jquery`。
- `xxx@版本号` 指定需要安装的版本号，若不指定将安装最新的稳定版本。

### npm uninstall 卸载（快捷方式：rm, r）

- `xxx` 卸载 xxx。多个依赖可用空格分割。
- `xxx -D` 卸载 xxx，并将依赖信息从 `package.json` 中的 `devDependencies` 中清除。

### npm list 列出已安装依赖（快捷方式：ls）

- 默认列出局部依赖。
- `npm list -g` 列出已安装的全局依赖。

### **npm outdated**** 检查过期依赖**

### npm update 更新依赖（快捷方式：up）

- `xxx` 局部更新 xxx。
- `xxx -g` 全局更新 xxx。

### npm root 查看依赖安装路径（也就是node_modules的路径）

- 默认查看局部安装路径。
- `-g` 查看全局安装路径。

### npm view 查看模块的注册信息

- `xxx versions` 列出 `xxx` 的所有版本， 如：`npm view jquery versions`。
- `xxx dependencies` 列出 `xxx` 的所有依赖， 如：`npm view gulp dependencies`。
