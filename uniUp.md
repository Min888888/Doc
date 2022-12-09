# uni-up

# 概念

 `uni-app` 是一个使用 [Vue.js](https://vuejs.org/) 开发所有前端应用的框架，开发者编写一套代码，可发布到iOS、Android、Web（响应式）、以及各种小程序（微信/支付宝/百度/头条/飞书/QQ/快手/钉钉/淘宝）、快应用等多个平台。 

uni，读 `you ni`，是统一的意思。

很多人以为小程序是微信先推出的，其实，DCloud才是这个行业的开创者。

DCloud于2012年开始研发小程序技术，优化webview的功能和性能，并加入W3C和HTML5中国产业联盟，推出了HBuilder开发工具，为后续产业化做准备。

2015年，DCloud正式商用了自己的小程序，产品名为“流应用”，它不是`B/S`模式的轻应用，而是能接近原生功能、性能的App，并且即点即用，第一次使用时可以做到边下载边使用。

为将该技术发扬光大，DCloud将技术标准捐献给工信部旗下的[HTML5中国产业联盟](https://www.html5plus.org/)，并推进各家流量巨头接入该标准，开展小程序业务。

 360手机助手率先接入，在其3.4版本实现应用的秒开运行。

部分公司接入了联盟标准，但更多公司因利益纷争严重，标准难以统一。

技术是纯粹的，不应该因为商业利益而分裂。开发者面对如此多的私有标准不是一件正确的事情。

造成混乱的局面非DCloud所愿。于是我们决定开发一个免费开源的框架。

既然各巨头无法在标准上达成一致，那么就通过这个框架为开发者抹平各平台差异。

这，就是uni-app的由来。 

DCloud的初心是什么？

1. **为开发者提供免费、高效的开发工具，让天下没有难做的应用**
2. **改进应用形态，让用户更方便的获取数字服务**

DCloud也再次承诺不会对uni-app、HBuilderX等工具收费，感谢数百万开发者的一路陪伴，也请一直监督我们不忘初心！



## 编译器

将单文件转换到对应的小程序多文件页面

## 运行时 MVVM

uni-app runtime : 连接小程序和vue的生命体系

数据委托 ：将vue的数据委托给小程序的appdata,渲染是小程序做的

事件代理：将小程序的事件函数代理到vue事件函数

生命周期：将小程序生命周期转到vue生命周期

## 性能优化

差量更新：在使用vue编写小程序时，会自动减少setData的频次，

数据量减少：基于差量更新，借鉴westore JSON Diff 库，不被响应的数据会被uni-up优化，比如list的下拉加载，使用角度直接可以this.data.push(...newData)去完成，框架做了背后优化；

## uni-app 开发体验如何？支持现代前端开发流程吗？

- 内置了webpack/vite
- NPM 包管理系统，详见[参考](http://uniapp.dcloud.io/tutorial/page-script#npm支持)
- es6+ 语法（发布时会自动编译为es5），详见[参考](http://uniapp.dcloud.io/tutorial/syntax-js#es6-支持)
- 各种预处理器（less、scss、stylus、typescript）
- uni-app的官方ide：HBuilderX，在vue、json、markdown、代码提示、操作效率上，有非常明显的优势，可帮助开发者大幅提高工作效率
- uni-app同时也提供了cli方式，可使用其他开发工具如vscode开发，当然开发效率不如HBuilderX。对比详见https://ask.dcloud.net.cn/article/35451
- HBuilder也提供了cli，[参考](https://hx.dcloud.net.cn/cli/README)

# 快速上手

HBuilderX: H是HTML的首字母，Builder是构造者，X是HBuilder的下一代版本。我们也简称`HX`。 `HX`是**轻如编辑器、强如IDE**的合体版本。 

1. 强大的语法提示 `HX`是中国唯一一家拥有自主IDE语法分析引擎的公司，对前端语言提供准确的代码提示和[转到定义](https://hx.dcloud.net.cn/Tutorial/UserGuide/goto?id=转到定义)(Alt+鼠标左键)
2. vue开发强化 `HX`对vue做了大量优化投入，开发体验远超其他开发工具
3.  `HX`支持java插件、nodejs插件，并兼容了很多vscode的插件及代码块。 

 如果你习惯了其他工具(如vscode或sublime)的[快捷键](https://hx.dcloud.net.cn/Tutorial/keybindings)，在菜单工具-快捷键方案中可以切换 

## 语法提示

1. 框架语法库是挂在项目下的，一个项目加载了一个框架语法库后，这个项目下所有js文件或HTML文件都会在代码助手提示这个框架的语法。
2. 但如果一个文件是单独从硬盘打开，没有整项目拖入hx，那么此时无法加载框架语法库。

## 语法帮助

 光标放到某api处，按下`F1`，就可跳转到这个api的官方手册。目前支持vue、uni-app、5+等api 。

常用文件可以添加到收藏夹

**sass/less插件配置小技巧：**

less、sass可以在插件配置里，配置为保存文件时自动编译。

```Json
{
  "onDidSaveExecution": true //重启生效sass插件
}
```

## 开发tip

1.  新的开发着应该使用rpx 

2.  很多开发者对响应式单位依赖太严重了 ， 你需要某元素的单位要根据屏幕**宽度**（小范围）大小变化时，才需要rpx这类动态宽度单位 ， 一般情况下高度和字体大小是不应该根据屏幕宽度（等比）变化的 

3.  使用`@import`语句可以导入外联样式表，`@import`后跟需要导入的外联样式表的相对路径，用`;`表示语句结束。 

4. style：静态的样式统一写到 class 中。style 接收动态的样式，在运行时会进行解析，请尽量避免将静态的样式写进 style 中，以免影响渲染速度。

5. ```css
   <!-- 设置页面背景颜色，使用 scoped 会导致失效 -- > 
     page {
   	background-color: #ccc;
   }
   ```

## uni-up 内置css变量

| CSS 变量            |          描述          | App                                                          | 小程序 | H5                   |
| :------------------ | :--------------------: | :----------------------------------------------------------- | :----- | :------------------- |
| --status-bar-height |     系统状态栏高度     | [系统状态栏高度](http://www.html5plus.org/doc/zh_cn/navigator.html#plus.navigator.getStatusbarHeight)、nvue 注意见下 | 25px   | 0                    |
| --window-top        | 内容区域距离顶部的距离 | 0                                                            | 0      | NavigationBar 的高度 |
| --window-bottom     | 内容区域距离底部的距离 | 0                                                            | 0      | TabBar 的高度        |

-  `var(--status-bar-height)` 此变量在微信小程序环境为固定 `25px`，在 App 里为手机实际状态栏高度 
- 当设置 `"navigationStyle":"custom"` 取消原生导航栏后，由于窗体为沉浸式，占据了状态栏位置。此时可以使用一个高度为 `var(--status-bar-height)` 的 view 放在页面顶部，避免页面内容出现在状态栏。
- 由于在 H5 端，不存在原生导航栏和 tabbar，也是前端 div 模拟。如果设置了一个固定位置的居底 view，在小程序和 App 端是在 tabbar 上方，但在 H5 端会与 tabbar 重叠。此时可使用`--window-bottom`，不管在哪个端，都是固定在 tabbar 上方。
-  目前 nvue 在 App 端，还不支持 `--status-bar-height`变量，替代方案是在页面 onLoad 时通过 uni.getSystemInfoSync().statusBarHeight 获取状态栏高度，然后通过 style 绑定方式给占位 view 设定高度。 
-  快速书写 css 变量的方法是：在 css 中敲 hei，在候选助手中即可看到 3 个 css 变量 

## 图片

使用本地路径背景图片需注意：

1. 为方便开发者，在背景图片小于 40kb 时，`uni-app` 编译到不支持本地背景图的平台时，会自动将其转化为 base64 格式；
2. 图片大于等于 40kb，会有性能问题，不建议使用太大的背景图，如开发者必须使用，则需自己将其转换为 base64 格式使用，或将其挪到服务器上，从网络地址引用。
3. 本地背景图片的引用路径推荐使用以 ~@ 开头的绝对路径。
4. 微信小程序不支持相对路径（真机不支持，开发工具支持）

## 字体图标

`uni-app` 支持使用字体图标，使用方式与普通 `web` 项目相同，需要注意以下几点：

- 支持 base64 格式字体图标。
- 支持网络路径字体图标。
- 小程序不支持在 css 中使用本地文件，包括本地的背景图和字体文件。需以 base64 方式方可使用。
- 网络路径必须加协议头 `https`。
- 从 [http://www.iconfont.cn](http://www.iconfont.cn/) 上拷贝的代码，默认是没加协议头的。
- 从 [http://www.iconfont.cn](http://www.iconfont.cn/) 上下载的字体文件，都是同名字体（字体名都叫 iconfont，安装字体文件时可以看到），在 nvue 内使用时需要注意，此字体名重复可能会显示不正常，可以使用工具修改。
- 使用本地路径图标字体需注意：
  1. 为方便开发者，在字体文件小于 40kb 时，`uni-app` 会自动将其转化为 base64 格式；
  2. 字体文件大于等于 40kb，仍转换为 base64 方式使用的话可能有性能问题，如开发者必须使用，则需自己将其转换为 base64 格式使用，或将其挪到服务器上，从网络地址引用；
  3. 字体文件的引用路径推荐使用以 ~@ 开头的绝对路径。

## [HBuilderX支持的项目运行说明](https://hx.dcloud.net.cn/Tutorial/Other/ProjectType?id=hbuilderx支持的项目运行说明)

HBuilderX支持多种项目类型，不同类型的项目的运行也是不一样的。如下是各种项目类型可以运行的一览表。

|                    | 普通web | uni-app | 5+ App | wap2app | 快应用 | 微信小程序 |
| ------------------ | ------- | ------- | ------ | ------- | ------ | ---------- |
| 运行到手机或模拟器 | ×       | √       | √      | √       | √      | ×          |
| 运行到浏览器       | √       | √       | √      | √       | ×      | ×          |
| 运行到小程序       | ×       | √       | ×      | ×       | ×      | √          |
| 运行到终端         | √       | √       | ×      | ×       | ×      | ×          |

- 如果你的项目类型不对，就无法运行到指定平台
- 项目类型的判断是根据项目根目录下的文件特征，比如manifest.json。如果导入HBuilderX的项目多了一层父目录，就无法识别正确的项目类型
- 对项目点右键，可以识别项目类型
- 可以在菜单工具-项目管理器图标主题中选“HBuilderX图标”，以直观的根据图标显示项目类型

## 快捷键

 `command+t`新建标签卡、

`command+shift+t`恢复刚关闭的标签卡、				

`command+w`关闭标签 

`command+p` 寻找文件

command是操作、command+shift是反操作或更多操作、command+alt为更多操作

`command+k`是格式化，那么`command+shift+k`就是合并为一行

`command+w`是关闭当前标签卡，那么`command+shift+w`是关闭所有标签卡

`command+f`是搜索，`command+alt+f`是目录内搜索



强化和鼠标的配合

`alt+鼠标滚轮`是横向滚动

`alt+鼠标单击`是转到定义

`alt+鼠标拖动`是列选择

`command+鼠标单击`是添加多光标

`鼠标双击`可以智能选中，详见选择菜单

## 项目创建

HBuilderX提供的免node开发，除了易用，还更高效。

- 新建项目：`Ctrl+N`
- 运行项目：`Ctrl+R`
- 发行项目：`Ctrl+U`

这比启动终端，移动焦点到终端窗口，敲命令快多了。

- 如果使用cli项目，那么less、scss、ts等编译器需要自己手动敲npm命令安装。由于DCloud官方不会和每种预编译器的每个版本都做兼容性测试，如果你使用了较低的预编译器版本，可能会无法正常运行，这需要你自己排查
- 如果使用HBuilderX可视化创建项目，这些编译器会按需自动安装，并且是DCloud官方测试过版本兼容性的。开发者只需在你的代码中使用这些预编译技术，剩下的HBuilderX会自动搞定。

- cli创建的项目，是传统的node项目结构。工程代码在src目录下，编译器在项目下，编译结果在dist目录下。
- HBuilderX可视化创建的项目，是一种免node开发概念。工程代码在项目目录下，编译器在HBuilderX目录下而不是项目下，编译结果在项目的unpackage目录下。

## 关于各端的管理规则需要耐心学习

uni-app并不难学，但我们注意到很多新人在适应各个平台的规则限制时比较急躁。

每个端，有每个端的管理规则，这不是uni-app在技术层面上可以抹平的：

- 比如H5端的浏览器有跨域限制；
- 比如微信小程序会强制要求https链接，并且所有要联网的服务器域名都要配到微信的白名单中；
- 比如App端，iOS对隐私控制和虚拟支付控制非常严格；
- 比如App端，Android、国产rom各种兼容性差异，尤其是因为谷歌服务被墙，导致的push、定位等开发混乱的坑；

遇事耐心，不急不躁，虽然这不是成功的唯一要素，但它是你技术路上长远走下去的基础。

# 条件编译

通过条件编译，可以保持对某端的特色支持, 条件编译是用特殊的注释作为标记，在编译时根据这些特殊的注释，将注释里面的代码编译到不同平台。 

 ![img](https://vkceyugu.cdn.bspapp.com/VKCEYUGU-f184e7c3-1912-41b2-b81f-435d1b37c7b4/29448a55-2785-4296-9248-913dbda9de7f.png) 

## 写法

 以 #ifdef 或 #ifndef 加 **%PLATFORM%** 开头，以 #endif 结尾。 

- \#ifdef：if defined 仅在某平台存在
- \#ifndef：if not defined 除了某平台均存在
- **%PLATFORM%**：平台名称

| 值                      | 生效条件                                                     |
| :---------------------- | :----------------------------------------------------------- |
| VUE3                    | HBuilderX 3.2.0+ [详情](https://ask.dcloud.net.cn/article/37834) |
| APP-PLUS                | App                                                          |
| APP-PLUS-NVUE或APP-NVUE | App nvue 页面                                                |
| H5                      | H5                                                           |
| MP-WEIXIN               | 微信小程序                                                   |
| MP-ALIPAY               | 支付宝小程序                                                 |
| MP-BAIDU                | 百度小程序                                                   |
| MP-TOUTIAO              | 字节跳动小程序                                               |
| MP-LARK                 | 飞书小程序                                                   |
| MP-QQ                   | QQ小程序                                                     |
| MP-KUAISHOU             | 快手小程序                                                   |
| MP-JD                   | 京东小程序                                                   |
| MP-360                  | 360小程序                                                    |
| MP                      | 微信小程序/支付宝小程序/百度小程序/字节跳动小程序/飞书小程序/QQ小程序/360小程序 |
| QUICKAPP-WEBVIEW        | 快应用通用(包含联盟、华为)                                   |
| QUICKAPP-WEBVIEW-UNION  | 快应用联盟                                                   |
| QUICKAPP-WEBVIEW-HUAWEI | 快应用华为                                                   |

## 支持的文件

- .vue
- .js
- .css
- pages.json
- 各预编译语言文件，如：.scss、.less、.stylus、.ts、.pug

注意点:

- 条件编译是利用注释实现的，在不同语法里注释写法不一样，js使用 `// 注释`、css 使用 `/* 注释 */`、vue/nvue 模板里使用 ``；
-  条件编译APP-PLUS包含APP-NVUE和APP-VUE，
- 使用条件编译请保证`编译前`和`编译后`文件的正确性，比如json文件中不能有多余的逗号；
- `VUE3` 需要在项目的 `manifest.json` 文件根节点配置 `"vueVersion" : "3"`

## static 目录的条件编译

|  目录名称   |     说明     |
| :---------: | :----------: |
|  app-plus   |     App      |
|     h5      |      H5      |
|  mp-weixin  |  微信小程序  |
|  mp-alipay  | 支付宝小程序 |
|  mp-baidu   |  百度小程序  |
|    mp-qq    |   QQ小程序   |
| mp-toutiao  |  字节小程序  |
|   mp-lark   |  飞书小程序  |
| mp-kuaishou |  快手小程序  |
|    mp-jd    |  京东小程序  |

专有目录下的静态资源只有在特定平台才会编译进去。

如以下目录结构，`a.png` 只有在微信小程序平台才会编译进去，`b.png` 在所有平台都会被编译。

```
┌─static
│  ├─mp-weixin
│  │  └─a.png
│  └─b.png
├─main.js
├─App.vue
├─manifest.json
└─pages.json
```

## 整体目录条件编译

 如果想把各平台的页面文件更彻底的分开，也可以在uni-app项目根目录创建`platforms`目录，然后在下面进一步创建`app-plus`、`mp-weixin`等子目录，存放不同平台的文件。

 **注意**

- `platforms`目录下只支持放置页面文件（即页面vue文件），如果需要对其他资源条件编译，建议使用[static 目录的条件编译](https://uniapp.dcloud.net.cn/tutorial/platform.html#static-目录的条件编译)。

## 语法高亮

 在 HBuilderX 中对条件编译的代码注释部分提供了语法高亮，可分辨出写法是否正确，使得代码更加清晰（独立js文件需在编辑器右下角切换javascript es6+编辑器，独立css文件暂不支持高亮，但不高亮不影响使用） 

## 正确注释和快速选中

在 HBuilderX 中，ctrl+alt+/ 即可生成正确注释（js：`// 注释`、css：`/* 注释 */`、vue/nvue模板： ``）。

## 注意

- Android 和 iOS 平台不支持通过条件编译来区分，如果需要区分 Android、iOS 平台，请通过调用 uni.getSystemInfo 来获取平台信息。支持`ifios`、`ifAndroid`代码块，可方便编写判断。
-  你的应用想分平台适配颜色，只有条件编译是代码量最低、最容易维护的。 
- 有些公司的产品运营总是给不同平台提不同需求，但这不是拒绝uni-app的理由。关键在于项目里，复用的代码多还是个性的代码多，正常都是复用的代码多，所以仍然应该多端。而个性的代码放到不同平台的目录下，差异化维护。

## H5-PLUS

uni-up封装了ios、android端的特色能力，通过js即可调用跨端能力

## nvue

是native view的缩写，在vx上补充了uni的js.api

## native.js

手机操作系统的原生对象转映射为js对象，在js里编写原生代码的技术

## uni - sdk

实现原生扩展

# 跨端

 跨端，不是把web的习惯迁移到全平台。而是按照uni的写法，然后全平台使用。 

## css

 非H5端不支持*选择器, body的元素选择器请改为page等

## 组件和页面样式相互影响

 非H5端默认并未启用 scoped，如需要隔离组件样式可以在 style 标签增加 scoped 属性，H5端为了隔离页面间的样式默认启用了 scoped 

# 组件

## easycom

 传统vue组件，需要安装、引用、注册，三个步骤后才能使用组件。`easycom`将其精简为一步。 只要组件安装在项目的components目录下，并符合`components/组件名称/组件名称.vue`目录结构。就可以不用引用、注册，直接在页面中使用。 

 不管components目录下安装了多少组件，`easycom`打包后会自动剔除没有使用的组件，对组件库的使用尤为友好。 

 在[uni-app插件市场](https://ext.dcloud.net.cn/)下载符合`components/组件名称/组件名称.vue`目录结构的组件，均可直接使用。 

 `easycom`只处理vue组件，不处理小程序专用组件（如微信的wxml格式组件）。不处理后缀为.nvue的组件。但vue组件也可以全端运行，包括小程序和app-nvue。 

## tabBar

如果应用是一个多 tab 应用，可以通过 tabBar 配置项指定一级导航栏，以及 tab 切换时显示的对应页。

在 pages.json 中提供 tabBar 配置，不仅仅是为了方便快速开发导航，更重要的是在App和小程序端提升性能。在这两个平台，底层原生引擎在启动时无需等待js引擎初始化，即可直接读取 pages.json 中配置的 tabBar 信息，渲染原生tab。

- 当设置 position 为 top 时，将不会显示 icon
- tabBar 中的 list 是一个数组，只能配置最少2个、最多5个 tab，tab 按数组的顺序排序。
- tabbar 切换第一次加载时可能渲染不及时，可以在每个tabbar页面的onLoad生命周期里先弹出一个等待雪花（hello uni-app使用了此方式）
- tabbar 的页面展现过一次后就保留在内存中，再次切换 tabbar 页面，只会触发每个页面的onShow，不会再触发onLoad。
- 顶部的 tabbar 目前仅微信小程序上支持。需要用到顶部选项卡的话，建议不使用 tabbar 的顶部设置，而是自己做顶部选项卡，可参考 hello uni-app->模板->顶部选项卡。

## uni  ui

 uni-app是有[内置组件](https://uniapp.dcloud.io/component/README)的。这和web开发不一样。web开发基本上不用基础组件，都是找一个三方ui库，全套组件都包含。那是因为html的基础组件默认样式不适配手机风格。但uni-app体系不是这样，内置组件就是为手机优化的。 

 但内置组件只能满足基础需求，更多场景，需要扩展组件。扩展组件是基于内置组件的二次封装，从性能上来讲，扩展组件的性能略低于内置组件，所以开发者切勿抛弃内置组件，直接全套用三方UI组件库。 

 uni-app的[插件市场](https://ext.dcloud.net.cn/)，有很多扩展组件，有的是单独的，有的是成套的。 

 组件分2大类：1、vue组件（文件后缀为vue）；2、小程序自定义组件（文件后缀为wxml或其他小程序平台特有后缀名称） 

小程序组件又分为：微信/QQ小程序组件、阿里小程序组件、百度小程序组件、字节跳动小程序组件。
这些组件uni-app都支持，但受组件本身技术特点限制，在不同端有不一样的支持度。下面这张表格，可以清楚的表达不同类型的组件的兼容性。

 ![img](https://ask.dcloud.net.cn/uploads/article/20200422/2b0f69a305534929951ef7b1bea847e6.jpg) 

 从表格中可以很明显看出，更推荐使用的是全端兼容的uni规范组件。 

插件市场，[https://ext.dcloud.net.cn](https://ext.dcloud.net.cn/)，有各种玲琅满目的组件、模板。
其中成套的全端兼容ui库包括：

- [uViewUI](http://www.uviewui.com/)：组件丰富、文档清晰，支持nvue
- [colorUI css库](http://ext.dcloud.net.cn/plugin?id=239)：颜值很高，css库而非组件
- [unify UI](https://ext.dcloud.net.cn/plugin?id=2251)：全端支持的组件库，侧重nvue
- [mypUI](https://ext.dcloud.net.cn/plugin?id=2190)：全端支持的组件库，侧重nvue
- [ThorUI组件库](https://ext.dcloud.net.cn/plugin?id=556)
- [graceUI商业库](http://grace.hcoder.net/)
- [nPro全端nvue组件与模版库](https://ext.dcloud.net.cn/plugin?id=5169)：云端一体、nvue优质商业库，https://ext.dcloud.net.cn/plugin?id=5169
- [first UI](https://ext.dcloud.net.cn/plugin?id=7646)：分开源版和商业版
- [图鸟UI](https://ext.dcloud.net.cn/plugin?id=7088)：高颜值UI库
- [s-ui](https://ext.dcloud.net.cn/plugin?id=4262)

综上，官方对组件的使用建议是：

1. 首先使用内置组件
2. 然后使用uni ui扩展组件
3. 其他需求依靠插件市场其他组件灵活补充

### 注意点

- tabbar 的 js api 见[接口-界面-tabbar](https://uniapp.dcloud.io/api/ui/tabbar)，可实现动态显示隐藏（如弹出层无法覆盖tabbar）、内容修改（如国际化）、item加角标等功能。hello uni-app中也有示例。
- 代码跳转到 tabbar 页面，api只能使用[uni.switchTab](https://uniapp.dcloud.io/api/router?id=switchtab)，不能使用uni.navigateTo、uni.redirectTo；使用navigator组件跳转时必须设置[open-type="switchTab"]
-  tabbar 的默认高度，在不同平台不一样。App端的默认高度在HBuilderX 2.3.4起从56px调整为50px，与H5端统一。开发者也可以自行设定高度，调回56px。 
- tabbar 在H5端是div模拟的，属于前端屏幕窗口的一部分，如果要使用bottom居底定位方式，应该使用css变量`--window-bottom`，比如悬浮在tabbar上方10px的按钮，样式如下`bottom: calc(var(--window-bottom) + 10px)`
- 如果是需要先登录、后进入tab页面，不需要把登录页设为首页，首页仍然是tabbar页，可参考[云端一体登录模板](https://ext.dcloud.net.cn/plugin?id=13)

# 启动模式

 启动模式配置，仅开发期间生效，用于模拟直达页面的场景，如：小程序转发后，用户点击所打开的页面。 

**属性说明：**

| 属性    | 类型   | 是否必填 | 描述                             |
| :------ | :----- | :------- | :------------------------------- |
| current | Number | 是       | 当前激活的模式，list节点的索引值 |
| list    | Array  | 是       | 启动模式列表                     |

**list说明：**

| 属性  | 类型   | 是否必填 | 描述                                                         |
| :---- | :----- | :------- | :----------------------------------------------------------- |
| name  | String | 是       | 启动模式名称                                                 |
| path  | String | 是       | 启动页面路径                                                 |
| query | String | 否       | 启动参数，可在页面的 [onLoad](https://uniapp.dcloud.net.cn/tutorial/page.html#lifecycle) 函数里获得 |

# 对比微信小程序原生开发

- 原来app.json被一拆为二。页面管理，被挪入了uni-app的pages.json；非页面管理，挪入了manifest.json
- 原来的app.js和app.wxss被合并到了app.vue中

# vue写法及其他注意事项

- H5 校验了更严格的 `vue` 语法，有些写法不规范会报警，比如： `data` 后面写对象会报警，必须写 `function`；不能修改 `props` 的值；组件最外层 `template` 节点下不允许包含多个节点等。
- CSS 內使用 `vh` 单位的时候注意 `100vh` 包含导航栏，使用时需要减去导航栏和 `tabBar` 高度，部分浏览器还包含浏览器操作栏高度，使用时请注意。
-  组件内（页面除外）不支持 `onLoad`、`onShow` 等页面生命周期 
- 为避免和内置组件冲突，自定义组件请加上前缀（但不能是 u 和 uni）。比如可使用的自定义组件名称：`my-view`、`m-input`、`we-icon`，例如不可使用的自定义组件名称：`u-view`、`uni-input`，如果已有项目使用了可能造成冲突的名称，请修改名称，另外微信小程序下自定义组件名称不能以 wx 开头。
- 使用`flex`布局时，直接给自定义组件的父元素设置为`display:flex`不能影响到自定义组件内部的根节点，需要设置当前自定义组件为`display:flex`才可以。
- vue3写法可不再依赖return data(){},直接响应式依赖即可
- uni.$emit、 uni.$on 、 uni.$once 、uni.$off 触发的事件都是 App 全局级别的，跨任意组件，页面，nvue，vue 等，注意创建和销毁
-  `uni-app` 支持在 template 模板中嵌套 `` 和 ``，用来进行 [列表渲染](https://uniapp.dcloud.net.cn/tutorial/vue-basics#listrendering) 和 [条件渲染](https://uniapp.dcloud.net.cn/tutorial/vue-basics#condition)。  ` block在不同的平台表现存在一定差异，推荐统一使用template  `。 
- js 文件不支持使用`/`开头的方式引入
- 为多端兼容考虑，建议优先从 [uni-app插件市场](https://ext.dcloud.net.cn/) 获取插件。直接从 npm 下载库很容易只兼容H5端。
- `@`开头的绝对路径以及相对路径会经过 base64 转换规则校验
- 支付宝小程序组件内 image 标签不可使用相对路径
- 若设计稿宽度为 750px，元素 A 在设计稿上的宽度为 100px，那么元素 A 在 `uni-app` 里面的宽度应该设为：`750 * 100 / 750`，结果为：100rpx。
- 若设计稿宽度为 640px，元素 A 在设计稿上的宽度为 100px，那么元素 A 在 `uni-app` 里面的宽度应该设为：`750 * 100 / 640`，结果为：117rpx。
- 若设计稿宽度为 375px，元素 B 在设计稿上的宽度为 200px，那么元素 B 在 `uni-app` 里面的宽度应该设为：`750 * 200 / 375`，结果为：400rpx。
-  使用`@import`语句可以导入外联样式表，`@import`后跟需要导入的外联样式表的相对路径，用`;`表示语句结束。
- vue3 使用组合式api [组合式api <script setup>](https://uniapp.dcloud.net.cn/tutorial/vue-composition-api.html#%E4%BD%BF%E7%94%A8-script-setup )

代码演示：只需要注意，创建项目时，在创建模板下方勾选vue3选项即可；

```
<template>
	<view class="content" @tap="taPage">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{href}}</text>
		</view>
	</view>
</template>

<script setup>
	import {
		ref
	} from "vue";
	
	import {
	    onLoad,
	    onShow
	  } from "@dcloudio/uni-app";
	  
	  const href = ref('https://uniapp.dcloud.io/component/README?id=uniui');
	
	  // onLoad 接受 A 页面传递的参数
	  onLoad((option) => {
	    console.log("B 页面 onLoad:", option); //B 页面 onLoad: {id: '1', name: 'uniapp'}
	  });
	
	  onShow(() => {
	    console.log("B 页面 onShow");
	  });
	  
	  const taPage = (e) =>{
			console.log(e);
	  }
	
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>

```

- App端和H5端支持 `v-html` ，微信小程序会被转为 `rich-text`，其他端不支持 `v-html` 。
-  小程序端不支持 `classObject` 和 `styleObject` 语法。 
- "(value, name, index) in object"   v-for => v , k , index

vue2=>API

https://uniapp.dcloud.net.cn/tutorial/syntax-uts.html#%E5%9F%BA%E6%9C%AC%E8%AF%AD%E8%A8%80%E5%92%8C%E5%BC%80%E5%8F%91%E8%A7%84%E8%8C%83