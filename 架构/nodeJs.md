# nvm

 nvm 全名 [node](https://so.csdn.net/so/search?q=node&spm=1001.2101.3001.7020).js version management，顾名思义是一个nodejs的版本管理工具。通过它可以安装和切换不同版本的nodejs。 

下载地址：

https://github.com/coreybutler/nvm-windows/releases

```js
nvm off                     // 禁用node.js版本管理(不卸载任何东西)
nvm on                      // 启用node.js版本管理
nvm install <version>       // 安装node.js的命名 version是版本号 例如：nvm install 8.12.0
nvm uninstall <version>     // 卸载node.js是的命令，卸载指定版本的nodejs，当安装失败时卸载使用
nvm ls                      // 显示所有安装的node.js版本
nvm list available          // 显示可以安装的所有node.js的版本
nvm use <version>           // 切换到使用指定的nodejs版本
nvm v                       // 显示nvm版本
nvm install stable          // 安装最新稳定版
```

国内镜像：

 *# 设置npm_mirror:*

 nvm npm_mirror https://npmmirror.com/mirrors/npm/ 

 *# 设置node_mirror:* 

nvm node_mirror https://npmmirror.com/mirrors/node/ 



v16.13.1