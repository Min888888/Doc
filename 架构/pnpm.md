# 背景

和npm与yarn没有区别，同属于包管理工具， 但它的独特之处在于 ，可以节约磁盘空间并提升安装速度。

使用 npm 时，依赖每次被不同的项目使用，都会重复安装一次。  而在使用 pnpm 时，依赖会被存储在内容可寻址的存储中，所以：

1. 如果你用到了某依赖项的不同版本，只会将不同版本间有差异的文件添加到仓库。 例如，如果某个包有100个文件，而它的新版本只改变了其中1个文件。那么 `pnpm update` 时只会向存储中心额外添加1个新文件，而不会因为仅仅一个文件的改变复制整新版本包的内容。
2. 所有文件都会存储在硬盘上的某一位置。 当软件包被被安装时，包里的文件会硬链接到这一位置，而不会占用额外的磁盘空间。 这允许你跨项目地共享同一版本的依赖。

因此，您在磁盘上节省了大量空间，这与项目和依赖项的数量成正比，并且安装速度要快得多！

 默认情况下，pnpm 使用软链的方式将项目的直接依赖添加进模块文件夹的根目录。 

其实在学习pnpm之初，我还希望大家可以观看一位前辈的博文[pnpm](https://www.51cto.com/article/720275.html)

[pnpm官网](https://pnpm.io/zh/motivation)

另外还有一些关键的英文文献：

1. **security.** Like Yarn, pnpm has a special file with all the installed packages’ checksums to verify the integrity of every installed package before its code is executed.
2. **offline mode.** pnpm saves all the downloaded package tarballs in a local registry mirror. It never makes requests when a package is available locally. With the `--offline` parameter, HTTP requests can be prohibited at all.
3. **speed.** pnpm is not only faster than npm, it is faster than Yarn. It is faster than Yarn both with cold and hot cache. Yarn copies files from cache whereas pnpm just links them from the global store.

# 通过 npm 安装

` npm install -g pnpm`

## 使用较短的别名

`pnpm` 可能很难输入，因此您可以使用较短的别名，例如 `pn`。

`在 Powershell (Windows) 中添加永久别名：[](https://pnpm.io/zh/installation#在-powershell-windows-中添加永久别名)

在具有管理员权限的 Powershell 窗口中，执行：

```text
notepad $profile.AllUsersAllHosts
```

这里如果是之前没用创建过profile.ps1，会提示是否新建，点是;

在 `profile.ps1` 文件里加入：

```text
set-alias -name pn -value pnpm
```

 保存文件然后关闭窗口。 您可能需要关闭任何打开的 Powershell 窗口才能使别名生效。 

# 命令行

有关更多信息，请参阅各个 CLI 命令的文档。 以下是简便的 npm 命令等效列表，可帮助您入门：

| npm 命令      | pnpm 等效                                        |
| ------------- | ------------------------------------------------ |
| `npm install` | [`pnpm install`](https://pnpm.io/zh/cli/install) |
| `npm i `      | [`pnpm add `]                                    |
| `npm run `    | [`pnpm `]                                        |

- `pnpm create`  从 `create-*` 或 `@foo/create-*` 启动套件创建项目。 
- `pnpm add <pkg>`   安装软件包
- `pnpm install 别名: i ` 添加依赖
- `pnpm update  别名: up, upgrade`  更新包
- `pnpm remove  别名: rm, uninstall, un` 删除包
- `pnpm link  别名: ln`   使当前本地包可在系统范围内或其他位置访问。 
- `pnpm unlink`   取消链接一个系统范围的`package` (相对于 [`pnpm link`](https://pnpm.io/zh/cli/link)). 
- `pnpm import`   `pnpm import` 从另一个软件包管理器的 lock 文件生成 `pnpm-lock.yaml`。 
- `pnpm rebuild`  别名： `rb`    重建一个`package`。 
- `pnpm prune`  移除不需要的`packages`。 
- `pnpm fetch`   此命令专门用于加速构建 docker 映像。  `pnpm fetch` 将通过提供仅从 lockfile 中下载包至虚拟存储中 
- `pnpm install-test  别名: `it`    执行 `pnpm install` 然后立即执行 `pnpm test`. 它使用参数和 [`pnpm install`](https://pnpm.io/zh/cli/install)完全相同. 
- `pnpm patch-commit <path>`   从目录中生成一个补丁（灵感来自 Yarn 中一个类似的命令）。 
- `pnpm audit`  检查已安装包的已知安全问题。 
- `pnpm list  别名:ls `    此命令会以一个树形结构输出所有的已安装`package`的版本及其依赖。 

## 运行脚本

- `pnpm run   别名: run-script`

# workspace 工作区

维护一个工作区，是前端工程化的任务， pnpm 内置了对单一存储库（也称为多包存储库、多项目存储库或单体存储库）的支持， 你可以创建一个 workspace 以将多个项目合并到一个仓库中。 

 一个 workspace 的根目录下必须有 [`pnpm-workspace.yaml`](https://pnpm.io/zh/pnpm-workspace_yaml) 文件， 也可能会有 [`.npmrc`](https://pnpm.io/zh/npmrc) 文件。 

自动化管理： 如果您正在思考如何管理 monorepo 项目，您可能还想看一下 [Bit](https://bit.dev/?utm_source=pnpm&utm_medium=workspace_page)。 Bit 在后台使用 pnpm，但将许多当前在由 pnpm/npm/Yarn 管理的传统工作区中手动完成的事情自动化。  

在未来我会实战一个自动化管理的workspace;



# 使用体验

学习了这么多，我们来创建一个vite项目来直观感受下npm with pnpm;

 `pn create vite@latest` 接下来按操作创建完成即可，创建完成后要安装依赖: `pn i` ;我事先准备了npm创建的项目，让我们通过图片来直观感受下他们的异同作为本篇的结尾; 

