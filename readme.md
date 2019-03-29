# lyo [![translate-svg]][translate-list] 

<!-- [![explain]][source]  -->
<!-- [![size-img]][size] -->

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/lyo-explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list
[size-img]: https://packagephobia.now.sh/badge?p=Name
[size]: https://packagephobia.now.sh/result?p=Name

「 Lyo是将Node.js模块变为,与浏览器兼容的库的最简单方法. 」

[中文](./readme.md) | [english](https://github.com/bokub/lyo)

---

## 校对 ✅

<!-- doc-templite START generated -->
<!-- repo = 'bokub/lyo' -->
<!-- time = '2018 9.18' -->
<!-- commit = 'd1749071c8a88789bd1e43ac666156ccfcfe05bb' -->
翻译的原文 | 与日期 | 最新更新 | 更多
---|---|---|---
[commit] | ⏰ 2018 9.18 | ![last] | [中文翻译][translate-list]

[last]: https://img.shields.io/github/last-commit/bokub/lyo.svg
[commit]: https://github.com/bokub/lyo/tree/d1749071c8a88789bd1e43ac666156ccfcfe05bb

<!-- doc-templite END generated -->


### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[If help, **buy** me coffee —— 营养跟不上了，给我来瓶营养快线吧! 💰](https://github.com/chinanf-boy/live-need-money)

---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


[![Lyo](https://i.imgur.com/nt5bYNJ.png)](https://github.com/bokub/lyo/issues/1)

> Node.js到浏览器模块 - 简单的方法

[![Npm version](https://runkit.io/bokub/npm-version/branches/master/lyo)](https://npmjs.com/package/lyo)
[![Build status](https://badgen.net/travis/bokub/lyo)](https://travis-ci.org/bokub/lyo)
[![Code coverage](https://badgen.net/codecov/c/github/bokub/lyo)](https://codecov.io/gh/bokub/lyo)
[![XO code style](https://badgen.net/badge/code%20style/XO/5ed9c7)](https://github.com/xojs/xo)

Lyo是将Node.js模块变为与浏览器兼容的库的最简单方法.

没有决策,不需要配置,它只是工作!

Lyo使用[Browserify][browserify],[babel][babel],[UglifyJS][uglify],还有一点魔力✨所以你不必担心配置问题

## Install & Run

```sh
# Install globally
npm i -g lyo

# Run
lyo
```

## Options

Lyo应该马上工作,但如果需要你可以用一些选项来帮它指路.

```
$ lyo --help

    Usage
      $ lyo [options]               运行 Lyo
      $ lyo init [options]          添加 Lyo 到你的项目{之后记得 npm i / yarn }
      $ lyo usage [options]         展示如何使用输出文件
      $ lyo get <module> [options]  使用 Lyo 从npm中获取文件并lyo化

    Options
      --input   -i  入口 文件
      --output  -o  输出 文件 / 文件夹
      --name    -n  在浏览器中的模块命名
      --banner  -b  在构建的浏览器捆绑文件中添加一个作者说明

    Examples
      $ lyo
      $ lyo -i main.js
      $ lyo -n runFunction
      $ lyo get query-string
      $ lyo -o dist/bundle.min.js
      $ lyo -b 'Lyo\nLicensed under MIT'
```

## 推荐的工作流程

一旦你在你的模块上尝试了Lyo并找到了可以使用的好选项,你应该考虑以下步骤

### 1. Add Lyo 到你的项目

运行`lyo init`(可带选项),编辑你的`package.json`, 如下:

-   Lyo将被添加到dev依赖项中
-   将创建(或编辑) pre-publish 脚本,以便在每个`npm publish`之前触发Lyo
-   如果您提供选项,**它们将保存为默认选项**

```sh
# 一些 随机 参数的例子
$ lyo init -i lib/main.js -n runMyModule
```

![package.json](https://i.imgur.com/yxBGqne.png)

别忘了之后运行`npm install/yarn`

### 2. Add 文档

运行`lyo usage`(带选项)展示示例代码段.您可以编辑,并将其包含在您的`README.md`.

```
$ lyo usage

> Edit and include the following snippet in your README.md
```

![HTML example](https://i.imgur.com/xryNOT5.png)

### 3. Commit 和  publish

Lyo将输出一个*捆绑*文件,默认情况下,在`dist`文件夹.您可以选择是否提交.这真的取决于你.

运行`npm publish`,Lyo将编译你的模块,捆绑包和你的模块的其余部分,将被推送到npm注册表.恭喜你,你已经完成了! 💪

### 一些 tips

-   不要在Node.js环境中使用bundle.该捆绑包应该只在浏览器中运行
-   如果Lyo无法编译您的代码,请不要立即责怪`Lyo`.错误可能来自[Browserify][browserify],[babel][babel]要么[UglifyJS][uglify]

## 在其他人的模块上使用 Lyo 

有时,您在没有浏览器兼容版本的情况下,偶然发现了npm模块.

不用担心,只是运行`lyo get <module>`立即下载并编译⚡

```sh
# 编译 query-string (npmjs.com/package/query-string)
$ lyo get query-string

# 编译 特定版本 的 Joi (npmjs.com/package/joi)
$ lyo get joi@13.5.0 --name Joi
```

* * *

## FAQ

#### 如果我需要lyo不支持的功能怎么办？

如果你需要Lyo不支持的功能(源地图,代码分割......),你最好的选择就是不使用Lyo,它只是一个一体化的软件包,具有自动配置功能.

但是,如果您认为Lyo应该支持此功能,请随时创建一个新功能[问题](https://github.com/bokub/lyo/issues)!

#### 为什么Lyo在有成千上万个更好的工具,还做同样的事情？

Lyo的哲学受到[XO](https://github.com/xojs/xo)高度启发,一个立即工作的`linter`,没有任何配置.XO只是一个ESLint包装器,但它可以省去选择ESLint规则的麻烦,然后还要将它们添加到一个新的`.eslintrc`文件,安装插件...... :cry:

我几乎所有的项目都使用XO,但是我找不到任何像XO一样简单的 Node.js > 浏览器 编译工具.这就是我创造Lyo的原因

#### Lyo是什么意思？

Lyo是[冻干](https://en.wiktionary.org/wiki/lyophilization)简称,一种将食物转化为干燥紧致形式的过程

## License

麻省理工学院©[Boris K.](https://github.com/bokub)

[browserify]: https://github.com/browserify/browserify

[babel]: https://github.com/babel/babel

[uglify]: https://github.com/mishoo/UglifyJS2
