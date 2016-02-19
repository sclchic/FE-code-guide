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
    * [模块化](#html-modularization)
3. [CSS相关规范](#css-standard)
    * [css语法](#css-grammar)
    * [书写规范](#writing-standard)
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

全部采用小写方式，以连接符分割，名称尽量简洁。
例如：chic-project-name

<a name="catalog-name"></a>
### 3.目录命名

参照项目命名规范，但是注意，统一不使用复数命名法。例如：命名为scripts, styles, images ...

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
### 5.缩进与换行规范

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
* 不要在自动闭合标签结尾处使用斜线([HTML5规范](http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag)指出他们是可选的)。
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

根据HTML5规范，通常在引入CSS和JS时不需要指明 **type**，因为 **text/css** 和 **text/javascript** 分别是他们的默认值。

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

<a name="html-modularization"></a>
## 模块化

* 每个模块必须有一个模块名
* 模块的子节点类名需带上模块名（防止模块间嵌套时产生不必要的覆盖）
* 孙辈节点无需再带模块名

<a name="css-standard"></a>
## CSS相关规范

<a name="css-grammar"></a>
### 1.css语法

* 使用小写标签名、属性名，属性名用中划线做分隔符。
* 在属性上，使用双引号，不要使用单引号。
* 不要在自动闭合标签结尾处使用斜线([HTML5规范](http://dev.w3.org/html5/spec-author-view/syntax.html#syntax-start-tag)指出他们是可选的)
* 不要省略可选的结束标签，省略不利于代码维护。例如：`</li>`, `</p>`。
* boolean属性指不需要声明取值的属性，XHTML需要每个属性声明取值，但是HTML5并不需要。[更多](https://html.spec.whatwg.org/multipage/infrastructure.html#boolean-attributes)

<a name="writing-standard"></a>
### 2.书写规范（主要是less书写）

* 每个属性声明末尾都要加分号

```
    .element {
        color: red;
    }
```

* 元素选择器用小写字母
* 去掉小数点前面的0
* 去掉数字中不必要的小数点和小数点前后的0

```
    .element {
        /* width: 50.0px; */
        width: 50px;
    }
```

* 同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法

```
    .element {
        -webkit-border-radius: 3px;
           -moz-border-radius: 3px;
                border-radius: 3px;
    
        background: -webkit-linear-gradient(top, #fff 0, #eee 100%);
        background:    -moz-linear-gradient(top, #fff 0, #eee 100%);
        background:         linear-gradient(to bottom, #fff 0, #eee 100%);
    }
```

* 无前缀的标准属性应该写在有前缀的属性后面
* 用 `border: 0;` 代替 `border: none;`
* 尽量少用 `*` 选择器
* 如无必要，省略 0 值单位。这些单位包括：

```
   %|em|ex|ch|rem|vw|vh|vmin|vmax|cm|mm|in|pt|pc|px
```

* 如无必要，省略 url 中的引号
* 不推荐使用 `id` 来书写样式
* 空格

```
    .element + p { /* '{'前需要空格；选择器'>', '+', '~'前后需要空格 */
        color: red !important; /* 属性名后面不需要空格，属性值前需要空格； `！important` '!'后不需要空格 */
        background-color: rgba(0, 0, 0, .5); /* 属性值中的','后需要空格；属性值'('后和')'前不需要空格 */
    }
```

* 空行

```
    .element, /* 多个规则的分隔符','后换行 */
     div { /* '}'后换行 */
        color: #fff;   
        /* 不同选择器的属性之间加空行 */
        p {
            background-color: #c00;  /* 每个属性单独一行 */
        }
        /* '}'之后加空行 */
    } /* '}'前换行 */
```

* 注释
less中统一使用 `/* 注释 */` 类型注释。

```
    .element {
        /* 缩进与下一行代码保持一致 */  
        width: 50px;
        color: red; /* color red */
    }
```

* 颜色
颜色16进制用小写字母；颜色16进制尽量用简写。

```
    .element {
        color: #abcdef;
        background-color: #012;
    }
```

* 属性简写
尽量分开写 `margin` `padding`

```
    .element {
        margin: 0 0 0 0;
        padding: 0 0 0 0;
    }
```

* 媒体查询
尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。

```
    .element {
        ...
    }
    
    .element-avatar{
        ...
    }
    
    @media (min-width: 480px) {
        .element {
            ...
        }
    
        .element-avatar {
            ...
        }
    }
```

* 特指less
    1.`import` 的文件不加 `.less`后缀，统一用双引号
    2. 嵌套层数尽量少，控制在5层以内
    
```
    @import "dialog";
```

<a name="css-name"></a>
### 3.命名规范

* 文件、class命名
    * 由单词、连接符( [扩展](http://blog.jobbole.com/67280/) )、数字组成，不允许使用拼音或者拼音缩写，甚至是拼音和英文混杂的形式，不允许以数字开头
    * 不依据表现形式来命名，可根据内容来命名，可根据功能来命名。
    * 保证缩写后还能较为清晰保持原单词所能表述的意思，使用业界熟知的或者约定俗成的。

* id采用驼峰式命名

<a name="hack-standard"></a>
### 4.hack规范

咱们只兼容IE8(包括IE8)以上的版本的浏览器；ie系列浏览器hack写法如下：

<table width="100%" border="1" cellspacing="0" cellpadding="0">
    <tr>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100"><strong>IE6</strong></td>
        <td valign="top" width="100"><strong>IE7</strong></td>
        <td valign="top" width="100"><strong>IE8</strong></td>
        <td valign="top" width="100"><strong>IE9</strong></td>
        <td valign="top" width="100"><strong>IE10</strong></td>
        <td valign="top" width="100"><strong>现代浏览器</strong></td>
    </tr>
    <tr>
        <td valign="top" width="100"><strong>*</strong></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230115-3317a1b2d8744119ba721e57981f05e4.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230118-3ed8adc1c72244afbf903e68da630ae9.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230118-beaef78954cd4a57a11e49611e9873ab.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230118-21f7874f37ed49c4918f324492ee9788.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
    </tr>
    <tr>
        <td valign="top" width="100"><strong>+</strong></td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230119-d6a347d67c55433cbd0c27e3a0381fc4.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230122-09e7e33f525a4b57aba01e74b6d209e3.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
    </tr>
    <tr>
        <td valign="top" width="100"><strong>-</strong></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230122-2af9923378514f54a95ce4d8de1aa598.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230122-5ccf4873cc684aab9ba9309837424c7b.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
    </tr>
    <tr>
        <td valign="top" width="100"><strong>!important</strong></td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230123-fca8bda6198548a1aecc3d1941cdd770.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230123-14c082392e4e4a1cb6f227d1cf15a538.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230123-b750ef4ce3d24cf388174e8fdaaa8395.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230123-750e257415fd4a43a3ad466de14c609e.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230123-22dca13fac5c4a2ba64c8ea59f059707.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230124-7d6a8dbffe314cc78561a7039414ecad.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230124-9c28bd9db76b4fe59feb132ebe7268f0.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230145-ba85ffbd0eef4f2aa25bcbe36b3abd3d.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230146-176770759bff40d59d08327d82029a29.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230146-cec9841a0a8647f0b352ff7fc148a6af.png" alt="image" width="36" height="36" border="0"></strong></a></td>
    </tr>
    <tr>
        <td valign="top" width="100"><strong>\9</strong></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230149-8404a97acf4d4925a9a6860e54219a52.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230149-c96f9cfc2c2046d6b956fabd7a9710d8.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230150-4ba6ba64c3794993b62f37321b074bcc.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230154-d9a308507753401699238764737930ec.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230155-78e49f3f30ef41dca3ec322f37abfc51.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230156-e80ca15057ed491f8bde64d3e9dfd323.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230156-8ceee87d70d3481598347a1ba99193da.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230156-4cc11537158849a88e14134c58b86749.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230156-4b0dddef3c4b4c0fa34589a69d603b55.png"><strong><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230156-94d93416b5e64f38bb3a9b8a27c53a4f.png" alt="image" width="36" height="36" border="0"></strong></a></td>
        <td valign="top" width="100">&nbsp;</td>
    </tr>
    <tr>
        <td valign="top" width="100"><strong>\0</strong></td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230157-cc73ef93c25a458fb40deaffed9a17b5.png"><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230157-cb6f463d139e4ff8a3845661eae3acaa.png" alt="image" width="36" height="36" border="0"></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230158-f15e6615d5a14f64ac76df5ea6c77018.png"><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230158-f0db39a870d1450dac83f72411663c78.png" alt="image" width="36" height="36" border="0"></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230158-1ba0189e4ccf46b3bea782a9e6c13e10.png"><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230158-9cc64a0377dd4453ad63d41aa9ed3bfc.png" alt="image" width="36" height="36" border="0"></a></td>
        <td valign="top" width="100">&nbsp;</td>
    </tr>
    <tr>
        <td valign="top" width="100"><strong>\9\0</strong></td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100">&nbsp;</td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230157-cc73ef93c25a458fb40deaffed9a17b5.png"><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230157-cb6f463d139e4ff8a3845661eae3acaa.png" alt="image" width="36" height="36" border="0"></a></td>
        <td valign="top" width="100"><a href="http://images.cnitblog.com/blog/349217/201308/30230157-cc73ef93c25a458fb40deaffed9a17b5.png"><img style="display: inline; border-width: 0px;" title="image" src="http://images.cnitblog.com/blog/349217/201308/30230157-cb6f463d139e4ff8a3845661eae3acaa.png" alt="image" width="36" height="36" border="0"></a></td>
        <td valign="top" width="100">&nbsp;</td>
    </tr>
</table>

<a name="modularization"></a>
### 5.模块化

* 每个模块必须是一个独立的样式文件，文件名与模块名一致
* 模块样式的选择器必须以模块名开头以作范围约定

<a name="split-picture"></a>
## 切图规范

<a name="picture-compression"></a>
### 1.图像压缩

#### 各种格式图片比较

<table border="1" cellspacing="0" cellpadding="5" width="100%">
    <tr>
        <td>格式</td>
        <td>压缩模式</td>
        <td>交错支持</td>
        <td>透明支持</td>
        <td>动画支持</td>
    </tr>
    <tr>
        <td>JPG</td>
        <td>有损压缩</td>
        <td>支持</td>
        <td>不支持</td>
        <td>不支持</td>
    </tr>
    <tr>
        <td>PNG</td>
        <td>无损压缩</td>
        <td>支持</td>
        <td>支持</td>
        <td>不支持</td>
    </tr>
</table>

<table border="1" cellspacing="0" cellpadding="5" width="100%">
    <tr>
        <td>格式</td>
        <td>最高支持色彩通道</td>
        <td>索引色编辑支持</td>
        <td>透明支持</td>
    </tr>
    <tr>
        <td>PNG8</td>
        <td>256色</td>
        <td>支持</td>
        <td>支持布尔透明</td>
    </tr>
    <tr>
        <td>PNG24</td>
        <td>约1600万色</td>
        <td>不支持</td>
        <td>支持8位（256阶）alpha透明</td>
    </tr>
</table>

#### 各种图片格式特性

* JPG的特性
    1. 支持摄影图像或写实图像的高级压缩，并且可利用压缩比例控制图像文件大小。
    2. 有损压缩会使图像数据质量下降，并且在编辑和重新保存JPG格式图像时，这种下降损失会累积。
    3. JPG不适用于所含颜色很少、具有大块颜色相近的区域或亮度差异十分明显的较简单的图片。
   
* PNG的特性
    1. 能在保证最不失真的情况下尽可能压缩图像文件的大小。
    2. png用来存储灰度图像时，灰度图像的深度可多到16位，存储彩色图像时，彩色图像的深度可多到48位，并且还可存储多到16位的α通道数据。
    3. 对于需要高保真的较复杂的图像，PNG虽然能无损压缩，但图片文件较大，不适合应用在Web页面上。
    
#### 实践中应该如何选择保存的图片格式

* 适合使用PNG格式的场景
    1. 图像上颜色较少，并且主要以纯色或者平滑的渐变色进行填充。
    2. 具备较大亮度差异以及强烈对比的简单图像。
    
* 适合使用JPG格式的场景
    1. 对于写实的摄影图像或是颜色层次非常丰富的图像采用JPG的图片格式保存一般能达到最佳的压缩效果。

* 对于gif格式，只要不是需要动画效果的地方强烈建议都采用PNG格式图片。

#### 有关ps压缩时参数的设置

* JPG的参数设置
    * 品质设置技巧
        1. 不要存100%品质的JPG格式图片。因为100%并不一定是最高的品质，而是一个优化算法的极限值，所以会增加不必要的文件大小。建议存储95%品质的图片就可以最大限度的降低失真。
        2. 谨慎使用50%品质以下的压缩率。使用50%以下品质存储时会采用额外的压缩算法而导致图片失真更严重，尤其是对于有高对比度的图片。

    * 默认勾选优化选项，视具体情况勾选连续

* PNG8的参数设置
    1. 一般情况下默认选择“可选择”项即可。
    2. 一般只在图片颜色过多产生失真的情况下才需要选择仿色。建议选择扩散仿色，可以适当调节仿色的百分比以达到最佳的效果。仿色度越高文件大小也越大。
    3. 对于尺寸和文件大小相对较大的图片建议勾选交错选项。
    
<a name="sprite"></a>
#### Sprite

* 建议将文件类型相同并且颜色重叠度高的图片进行合并，一方面可以尽量减少体积。另一方面，因为图片使用颜色限制（PNG-8 和 GIF 最多 256 色），
太多的颜色可能导致图片失真；对于 JPG 类图片，也可能因为图片过大而压缩导致失真。
* 让图标尽量排列得有规律 -- 有规律地排放的图标跟容易定位和维护, 这里的间隔可以使用 16, 32, 48, 96 等标准尺寸。
* 将背景颜色一致的图标放置在一起 -- 如果背景颜色不一样, 最好分为两个或多个图片放置, 特别是背景颜色相近的, 很容易混淆。
* 将相同栏目的图标放置在一起 -- 这样可以少写一些 CSS 代码. 设置一个 background, 再在每个项设置 background-position 就行了。
* 不要将大图绑在一块 -- 大部分用户都不会耐心地等待页面的所以文件被下载完毕再进行阅读, "不耐烦" 会驱使他们去点 close。

<a name="iconfont"></a>
### Iconfont

待续。。。
