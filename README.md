# cloud-native-guild

从零开始的云原生笔记仓库。

这个仓库使用 [docsify](https://docsify.js.org/) 组织 Markdown 笔记，并计划通过 GitHub Pages 直接发布 `docs/` 目录。

## 目录结构

```text
.
├── docs/
│   ├── index.html          # docsify 入口页
│   ├── README.md           # 站点首页
│   ├── _sidebar.md         # 左侧导航
│   ├── .nojekyll           # GitHub Pages 静态发布标记
│   ├── assets/             # 图片等静态资源
│   └── notes/              # 云原生笔记文章
│       └── 0.网站介绍.md    # 第一篇文章
├── .gitignore
├── LICENSE
└── README.md
```

## 如何编写文章

1. 在 `docs/notes/` 目录下新建 Markdown 文件，例如：

   ```text
   docs/notes/1.Kubernetes基础.md
   docs/notes/2.容器网络.md
   ```

2. 文章使用普通 Markdown 语法即可：

   ```markdown
   # Kubernetes 基础

   ## Pod

   Pod 是 Kubernetes 中最小的调度单元。
   ```

3. 新文章写完后，更新 `docs/_sidebar.md`，把文章加入导航：

   ```markdown
   - [网站介绍](notes/0.网站介绍.md)
   - [Kubernetes 基础](notes/1.Kubernetes基础.md)
   - [容器网络](notes/2.容器网络.md)
   ```

4. 图片等静态资源建议放在 `docs/assets/` 下，然后在文章中引用：

   ```markdown
   ![架构图](../assets/example.png)
   ```

   这里的路径是相对于 `docs/notes/` 下的文章而言的。如果文章后续放进更深的子目录，需要相应调整相对路径。

## 如何使用 docsify

docsify 不需要构建，浏览器会直接加载 `docs/` 里的 Markdown 文件并渲染成文档站点。

本地预览可以使用 docsify-cli：

```bash
npm install -g docsify-cli
docsify serve docs
```

启动后访问：

```text
http://localhost:3000
```

也可以不全局安装，直接使用 npx：

```bash
npx docsify-cli serve docs
```

核心文件说明：

- `docs/index.html`：docsify 配置和页面入口。
- `docs/README.md`：访问站点根路径时显示的首页内容。
- `docs/_sidebar.md`：左侧导航目录。
- `docs/notes/`：存放正式笔记文章。
- `docs/assets/`：存放图片等静态资源。
- `docs/.nojekyll`：告诉 GitHub Pages 不要用 Jekyll 处理站点，避免 `_sidebar.md` 这类下划线文件被忽略。

## 如何部署到 GitHub Pages

这个仓库已经按 GitHub Pages 的 `/docs` 发布方式准备好静态文件。

部署步骤：

1. 将代码推送到 GitHub。
2. 进入仓库页面的 `Settings`。
3. 打开 `Pages`。
4. 在 `Build and deployment` 中选择 `Deploy from a branch`。
5. Branch 选择 `main`，目录选择 `/docs`。
6. 保存后等待 GitHub Pages 自动发布。

之后每次修改 `docs/notes/` 下的文章并推送到 `main` 分支，GitHub Pages 都会自动更新站点。
