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
### 文档目录结构

<a name="project-name"></a>
### 项目命名

全部采用小写方式，以下划线分割,名称尽量简洁。
例如：chic_project_name

<a name="catalog-name"></a>
### 目录命名

参照项目命名规范；
但是注意，统一不使用复数命名法。
例如：命名为scripts, styles, images ...

<a name="notes"></a>
### 注释

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
### 缩进与换行规范

保持统一的代码缩进风格，有利于代码的阅读，也可以避免在 Git 等版本管理工具中造成冗余的 diff 信息。最重要的是千万不要空格和制表符（TAB）混用。
有 [血淋淋的教训](https://github.com/cssmagic/blog/issues/22 ) 啊！

    使用4个空格缩进
    使用Unix风格换行符（LF）保证跨平台的一致性
    删除行尾多余空格
    文件末尾增加一个空行

#### 如何保证统一的缩进风格

    统一团队成员编辑器设置
    利用 **EditorConfig**  统一，快速开始
        1. 在项目中根目录新建一个 .editorconfig 文件，保存为 utf-8 格式。Windows 用户由于无法直接新建一个只有扩展名的文件，新建的时候在末尾多加一个点 即可（.editorconfig. ），也可以在命令行（CMD）中使用 echo.>.editorconfig 来创建。
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
