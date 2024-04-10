### 你需要什么

- [Node.js](https://nodejs.org/en/download/) 18.0或以上版本version 18.0 or abov:
  - 安装Node.js时，建议您选中与依赖项相关的所有复选框。
- yarn

## 生成一个新站点

使用**classic template**生成一个新的Docusaurus站点。

运行以下命令后，classic模板将自动添加到项目中：

```bash
yarn create docusaurus
```

您可以在命令提示符、Powershell、终端或代码编辑器的任何其他集成终端中键入此命令。

该命令还安装运行Docusaurus所需的所有必要依赖项。

## Running the development server

要实时预览你的编辑，你可以运行本地开发服务器。它会部署你的网站，并反映最新更改。

```bash
cd your-website
yarn start
```

`yarn start`命令在本地构建您的网站，并通过开发服务器提供服务，您可以在http://localhost:3000/上查看。

打开 “docs/intro.Md” (此页面) 并编辑一些行: 网站会自动重新加载并显示您的更改。

## Build

Docusaurus 是一款现代化的静态网页生成器。因此，我们需要将网站生成为静态内容，并上传到网络服务器，才能被其他人访问。 要构建站点，请使用以下命令：

```bash
yarn build
```

内容将会在 `/build`目录下生成, 它可以复制到任何静态文件托管服务，如GitHub页面、Vercel或Netlify。查看部署文档以了解更多详细信息。

## 升级 Docusaurus 版本

使用 yarn 命令:

```bash
yarn add @docusaurus/core @docusaurus/preset-classic
```

:::tip

执行 `yarn add @docusaurus/core @docusaurus/preset-classic` 命令不仅可以用于最初添加 Docusaurus 到你的项目中，还可以用来更新 Docusaurus 的版本。这是因为，当你运行这个命令时，Yarn 会做以下几件事：

1. **检查当前版本**：Yarn 首先检查你项目中 `package.json`文件里列出的 `@docusaurus/core`和 `@docusaurus/preset-classic`的当前版本。
2. **查询最新版本**：然后，Yarn 会查询这些包的最新版本。如果你没有指定版本号（就像这个命令一样），Yarn 默认会查找并安装最新的稳定版本。
3. **更新 `package.json`和 `yarn.lock`**：如果发现更高的版本，Yarn 会更新你的 `package.json`文件中的版本号，并且在 `yarn.lock`文件中锁定这些新版本的确切版本号。这确保了项目的其他开发者或者在其他环境中安装依赖时，能够获取到相同版本的依赖包，从而保持环境的一致性。
4. **下载并安装**：最后，Yarn 会下载并安装这些新版本的包到你的 `node_modules`目录下。

:::

## 网站结构

假设您选择了经典模板并将站点命名为 `my—website`，您将看到以下文件在一个新目录 `my—website/`下生成：

```blank
my-website
├── blog
│   ├── 2019-05-28-hola.md
│   ├── 2019-05-29-hello-world.md
│   └── 2020-05-30-welcome.md
├── docs
│   ├── doc1.md
│   ├── doc2.md
│   ├── doc3.md
│   └── mdx.md
├── src
│   ├── css
│   │   └── custom.css
│   └── pages
│       ├── styles.module.css
│       └── index.js
├── static
│   └── img
├── docusaurus.config.js
├── package.json
├── README.md
├── sidebars.js
└── yarn.lock
```

### [项目结构概要](https://docusaurus.io/zh-CN/docs/installation#project-structure-rundown)

- `/blog/` - 包含博客降价文件。如果您禁用了博客插件，您可以删除该目录，或者您可以在设置 `path`选项后更改其名称。有关更多详细信息，请参见 [blog guide](https://docusaurus.io/zh-CN/docs/blog)
- `/docs/` - 包含文档的 Markdown 文件。 在 `sidebars.js`中自定义文档侧边栏的顺序. 如果您禁用了文档插件，您可以删除该目录，或者您可以在设置 `path`选项后更改其名称。有关更多详细信息，请参见 [docs guide](https://docusaurus.io/zh-CN/docs/docs-introduction)
- `/src/` - 非文档文件，如页面或自定义React组件。 严格来说，你不一定要把非文档类文件放在这里。不过把它们放在一个集中的目录，可以让代码检查或者处理更为简便。
  - `/src/pages` - 此目录中的任何JSX/TSX/MDX文件都将转换为网站页面. 有关更多详细信息，请参见 [pages guide](https://docusaurus.io/zh-CN/docs/creating-pages)
- `/static/` - 静态目录。这里的任何内容都将被复制到最终的 `build`目录的根目录中
- `/docusaurus.config.js` - 包含站点配置的配置文件。
- `/package.json` - Docusaurus网站是一个React应用程序. 你可以安装并使用任何 npm 包。
- `/sidebars.js` - 文档用于指定侧栏中文档的顺序
