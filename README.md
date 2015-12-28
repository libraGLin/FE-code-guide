# 前端开发规范指南

## 目录

1. [通用规范](#universal-standard)
    * [文档目录结构](#directory)
    * [项目命名](#project-name)
    * [目录命名](#catalog-name)
    * [注释](#notes)
    * [缩进与换行规范](#indentation-newline)
2. [HTML相关规范](#html-standard)
    * [语法](#grammar)
    * [文档类型](#doctype)
    * [lang属性](#lang)
    * [meta标签](#meta)
    * [title标签](#title)
    * [引入css,js](#reference-file)
    * [标签语义化](#label-semantics)
    * [通用模板](#general-template)
3. [CSS相关规范](#css-standard)
    * [css语法](#css-grammar)
    * [书写规范](#writing-standard)
    * [less使用规范](#less-standard)
    * [命名规范](#css-name)
    * [hack规范](#hack-standard)
    * [模块化](#modularization)
4. [JS相关规范](#js-standard)
5. [切图规范](#split-picture)
    * [图像压缩](#picture-compression)
    * [Sprite](#sprite)
    * [Iconfont](#iconfont)
5. [编辑器配置说明](#editor-configuration)
6. [前端构建工具说明](#construction-tool)
7. [最后说说](#final-chat)

<a name="universal-standard"></a>
## 通用规范

<a name="directory"></a>
### 1.文档目录结构

<a name="project-name"></a>
### 2.项目命名

全部采用小写方式，以下划线分割,名称尽量简洁。
例如：chic_project_name

<a name="catalog-name"></a>
### 3.目录命名

参照项目命名规范；
但是注意，统一不使用复数命名法。
例如：命名为scripts, styles, images ...

<a name="notes"></a>
### 4.注释

良好的注释使代码更具有可读性和可维护性，在多人协作的项目中，让团队成员秒懂代码意图。注释风格应当相对简洁，规范如下：

* 区块注释放在单独一行
* 保持注释内代码的缩进
* 为了注释文字更具有可读性，合理控制每行的字数，推荐每行80个字符（40个汉字以内）

> 通过webstorm设置私人快捷模板的方式可以快速生成所要的注释格式，如果是其他编辑器自行安装插件,自动生成注释。

#### 注释的种类

##### Doxygen 风格的注释

**每个文件**头部或者区块的开始处应当包含 [Doxygen](http://zh.wikipedia.org/wiki/Doxygen) 风格的注释，来阐明该文件或这段代码的作用、实现的特殊思路、作者、最后更新时间等信息。

    /**
     * @file  : 文件信息
     * @author: Chic
     * @update: 日/月/年
     * @note  : 注解
     * @doc   : 相关文档
     *
     * 这里是更详细的描述，当然我们要把字数控制在每行80个字符（40个汉字）以内。如果
     * 一行写不下，需要另起一行。
      <div class="mod">
          <p>代码展示说明</p>
      </div>
     */
     
##### 单行注释

    // 注释内容
    
##### 区块注释

> 注释横线的长度为80个字符，作为换行参考。

    /* ==========================================================================
       一级区块注释
       ========================================================================== */
       
    /* --------------------------------------------------------------------------
       二级区块注释
       -------------------------------------------------------------------------- */

##### ejs中的注释

    <% // 编译后的html中不显示的注释 %>
    <% /* 
          多行注释
          编译后的html中不显示的注释
     */ %>
     
    <!-- 编译后的html中显示的注释 -->

<a name="indentation-newline"></a>
### 4.缩进与换行规范

保持统一的代码缩进风格，有利于代码的阅读，也可以避免在 Git 等版本管理工具中造成冗余的 diff 信息。最重要的是千万不要空格和制表符（TAB）混用。
有 [血淋淋的教训](https://github.com/cssmagic/blog/issues/22 ) 啊！

* 使用4个空格缩进
* 使用Unix风格换行符（LF）保证跨平台的一致性
* 删除行尾多余空格
* 文件末尾增加一个空行

#### 如何保证统一的缩进风格

* 统一团队成员编辑器设置
* 利用 **EditorConfig**  统一，快速开始
    1. 在项目中根目录新建一个 .editorconfig 文件，保存为 utf-8 格式。Windows 用户由于无法直接新建一个只有扩展名的文件，
    新建的时候在末尾多加一个点 即可（.editorconfig. ），也可以在命令行（CMD）中使用 echo.>.editorconfig 来创建。
    2. 编辑 .editorconfig 文件
    3. 安装编辑器插件
        
推荐配置：

    # editorconfig.org
    root = true
    
    [*]
    charset = utf-8
    indent_style = space
    indent_size = 4
    end_of_line = lf
    trim_trailing_whitespace = true
    insert_final_newline = true

> EditorConfig使用详见 [官网](http://editorconfig.org/)

<a name="html-standard"></a>
## HTML相关规范

<a name="grammar"></a>
### 1.语法

* 使用小写标签名、属性名，属性名用中划线做分隔符。
* 在属性上，使用双引号，不要使用单引号。
* 不要在自动闭合标签结尾处使用斜线([HTML5规范](http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag)指出他们是可选的)
* 不要省略可选的结束标签，省略不利于代码维护。例如：`</li>`, `</p>`。
* boolean属性指不需要声明取值的属性，XHTML需要每个属性声明取值，但是HTML5并不需要。[更多](https://html.spec.whatwg.org/multipage/infrastructure.html#boolean-attributes)

<a name="doctype"></a>
### 2.文档类型

> 在页面开头使用这个简单地doctype来启用标准模式，使其在每个浏览器中尽可能一致的展现；
  虽然doctype不区分大小写，但是按照惯例，doctype大写   

    <!DOCTYPE html>

<a name="lang"></a>
### 3.lang属性

> 在html标签上加上lang属性，这会给语音工具和翻译工具帮助，告诉它们应该怎么去发音和翻译。

    <html lang="zh">
        ...
    </html>

更多关于 **lang** 属性的说明 [在这里](http://www.w3.org/html/wg/drafts/html/master/dom.html#attr-lang)
。在sitepoint上可以查到 [语言列表](http://www.sitepoint.com/web-foundations/iso-2-letter-language-codes/)
但sitepoint只是给出了语言的大类，例如中文只给出了zh，但是没有区分香港，台湾，大陆。而微软给出了一份更加 [详细的语言列表](https://msdn.microsoft.com/en-us/library/ms533052(v=vs.85).aspx)，
其中细分了zh-cn, zh-hk, zh-tw。

<a name="meta"></a>
### 4.meta标签

> 通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为 `UTF-8`，尽量将其作为 `head` 的第一个子元素。

```
    <meta charset="UTF-8">
```

> 优先使用IE最新版本([这个回答很不错](http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e))

```
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
```

> 为移动设备添加 `viewport`

```
    <meta name ="viewport" content ="initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no">
```

> 设置360浏览器为急速内核模式: `webkit` 为急速内核，`ie-comp` 为IE兼容内核，`ie-stand` 为IE标准内核。

```
    <meta name="renderer" content="webkit">
```

> 每个页面都应有一个不超过150个字符且能准确反映网页内容的描述标签，[文档](https://msdn.microsoft.com/zh-cn/library/ff723911(v=expression.40).aspx)

```
    <meta name="description" content="不超过150个字符">
```

> 页面关键字

```
    <meta name="keywords" content="">
```

> 定义网页作者

```
    <meta name="author" content="name, email">
```

> 禁止百度转码

```
    <meta http-equiv="Cache-Control" content="no-siteapp">
```

<a name="title"></a>
### 5.title标签

推荐紧随 `<meta charset>` 标签之后，让浏览器优先获取页面标题。

<a name="reference-file"></a>
### 6.引入css,js

根据HTML5规范, 通常在引入CSS和JS时不需要指明 **type**，因为 **text/css** 和 **text/javascript** 分别是他们的默认值。

#### HTML5 规范链接

* [使用link](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
* [使用style](http://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
* [使用script](http://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)

<a name="label-semantics"></a>
### 7.标签语义化

* 根据HTML元素的本身语义去使用他们。
* 禁止使用HTML5规范中被废弃的用于表现的标签，如下：

```
    basefont big blink center font marquee multicol nobr spacer tt
```

* 部分标签在HTML5中被重新定义或修改了语义，选择使用时要弄清语义，酌情使用。

#### 语义化

* `dl` 元素：现在代表一组名称与值的关联列表，并且不再适用于聊天和对话，纯粹的对话推荐使用`p`。
* `b` 元素：HTML5 中代表一段文本，这段文本仅仅出于功利的目的被提请注意，这种目的里没有传达任何额外的重要性，也没有交替的语言和心情的意味，比如文档摘要的关键字，
审查中的产品名，文本驱动的交互软件的可操作词，或文章的导引。
* `strong` 元素：HTML5 中代表强烈的重要性、严重性或内容的紧迫性。`strong` 不会改变 **所在句子的语意**，`em` 则会改变所在句子的语义。
* `i` 元素：HTML5 中赋予了新的语义，用来表示一段有着交替的语言和心情意味的文本，或者用来表明一种不同的文本质量的方式偏离平常的散文，比如分类命名，技术术语，其它语言的惯用短语，
一个念头，画外音，或西文的船名。
* `figure` 元素：不仅仅是用来标记图片，可以是音频、视频、代码、引用、表格等。而且只有当这些内容属于文档一部分时，才应该使用 figure 元素包裹起来。

> 无论如何，我们应当牢记，不应该使用 b 或 i 来实现加粗或倾斜的样式。只有在没有更适合的文本元素时，才使用 b, i 元素。例如：

* `em` 可以表示强调或重读。
* `strong` 可以表示重要性。
* `mark` 可以表示相关性。
* `cite` 可以标记著作名，如一本书、剧本或是一首歌。
* `dfn` 可以标记术语的定义实例。
* `var` 可以标记数学变量。

> 为了提高可访问性，`img` 标签最好添加有意义的 `alt` 文案.

[更多](http://html5doctor.com/)

<a name="general-template"></a>
### 8.通用模板

```
    <!DOCTYPE html>
    <html lang="zh">
    <head>
        <meta charset="UTF-8">
        <title>Chic</title>
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="renderer" content="webkit">
        <meta name ="viewport" content ="initial-scale=1, maximum-scale=3, minimum-scale=1, user-scalable=no">
        <link rel="stylesheet" href="chic.css">
    </head>
    <body>
        <script src="index.js"></script>
    </body>
    </html>
```
