title: sublime plugins for react
date: 2016-04-09 01:21:15
tags:
---
一些react开发的sublime插件
----------------------
### jsformat

1.  按下快捷键 Ctrl+Alt+p 打开Package Control命令面板

2.  输入 jsformat 回车安装即可.

3.  在你写javascript代码时,选中需要格式化的代码，按下 Ctrl+Alt+f 快捷键后,js代码自动格式化对齐,赶快试一试吧!

4.  如果上面的快捷键使用无效可以使用命令格式化代码,你可以选中要格式化的代码 ,然后按下 Ctrl+Alt+P (mac 系统 command + shift +p) 输入命令: Format:javascript 回车即可格式化.

### Terminal

Terminal : 在sublime中打开终端并定位到当前目录，神器，mac下的快捷键为：command+shift+T

### emmet

1.  Emmet 的基本用法是：输入简写形式，然后按 Tab 键。

2.  关于 Emmet 的更多用法，请看官方文档，这份[速查表](http://docs.emmet.io/cheat-sheet/)可以帮你快速记忆简写形式。

3.  Emmet安装：在Package Control中 install Package -> Emmet 安装Emmet.

4.  使用：输入特定含义的字符 按 Tag 自动完成

### react 插件
1.  **babel** 支持ES6，React.js, jsx代码高亮，对 JavaScript, jQuery 也有很好的扩展

    *   安装：PC上ctrl+shift+p（MacCmd+shift+p）打开面板输入babel安装

    *   配置：打开.js, .jsx 后缀的文件;

        ```
          打开菜单view，
          Syntax -> Open all with current extension as... -> Babel -> JavaScript (Babel)，
          选择babel为默认 javascript 打开syntax
        ```

2.  **sublimeLinter-jsxhint** JSX 代码审查，实时提示语法错误, 帮助快速定位错误

    *   安装PC上 ctrl+shift+p（MacCmd+shift+p）打开面板输入sublimeLinter-jsx安装(`请先确保sublimeLinter安装成功`)

    *   必须有node.js环境支持 安装node.js

    *   安装node中安装jsxhint
        npm install -g jsxhint

3.  **修改Emmet兼容jsx 文件(使用Tag 快速完成react 代码书写)**

    <div class="image-package imagebubble" widget="ImageBubble">![](http://upload-images.jianshu.io/upload_images/951996-bda01f6a6cc13ff1.jpg?imageMogr2/auto-orient/strip)

    <div class="image-caption">JSX语法书写</div>

    </div>

    *   安装PC上 ctrl+shift+p（MacCmd+shift+p）打开面板输入emmet安装

    *   使用方法 打开preferences -> Key bindings - Users，把下面代码复制到[ ]中括号内部(`注意配置文件为数组形式`)。

        ```
          {
              "keys": [
                  "super+e"
              ],
              "args": {
                  "action":"expand_abbreviation"
              },
              "command":"run_emmet_action",
              "context": [{
                  "key":"emmet_action_enabled.expand_abbreviation"
              }]
          },
          {
              "keys": ["tab"],
              "command":"expand_abbreviation_by_tab",
              "context": [{
                  "operand":"source.js",
                  "operator":"equal",
                  "match_all": true,
                  "key":"selector"
              }, {
                  "key":"preceding_text",
                  "operator":"regex_contains",
                  "operand":"(\b(a\b|div|span|p\b|button)(\.\w*|>\w*)?({FNXX==XXFN}*?}$)?)",
                  "match_all": true
              }, {
                  "key":"selection_empty",
                  "operator":"equal",
                  "operand": true,
                  "match_all": true
              }]
          }
        ```

        *   使用super+e触发 emmet；
        *   正则判断用 a，div，span，p，button标签默认tab 触发；
        *   默认 class 修改为 className 注 supre+e 在 PC 上指的是win+e（pc 建议修改为emmet 默认按键 ctrl+e）,在 mac 上指的是cmd+e
        *   详细请参考规则来源[StackOverflow](http://stackoverflow.com/questions/26089802/in-sublime-text-3-how-do-you-enable-emmet-for-jsx-files)，正则小有修改

4.   [JsFormat](https://github.com/jdc0589/JsFormat) 格式化 js 代码

jsformat 是 sublime 上 js 格式化比较好用的插件之一，通过修改它的`e4x` 属性可以使它支持 jsx。

### 安装

PC上`ctrl+shift+p`（Mac`Cmd+shift+p`）打开面板输入`JsFormat`安装.

### 使用

打开`preferences -> Package Settings -> JsFormat -> Setting - Users`,输入以下代码：

<pre>

<div class="widget-codetool" style="display: none;"><button class="selectCode btn btn-xs">全选</button><button href="javascript:void(0);" class="copyCode btn btn-xs" data-clipboard-text="{
  &quot;e4x&quot;: true,
  // jsformat options
  &quot;format_on_save&quot;: true,
}" data-toggle="tooltip" data-placement="bottom" title="">复制</button><button href="javascript:void(0);" class="saveToNote btn btn-xs">放进笔记</button></div>

`{
  "<span class="hljs-attribute">e4x</span>": <span class="hljs-value"><span class="hljs-literal">true</span></span>,
  // jsformat options
  "<span class="hljs-attribute">format_on_save</span>": <span class="hljs-value"><span class="hljs-literal">true</span></span>,
}`</pre>

即可保存时自动格式化，并支持 jsx 类型文件.

5.    SublimeCodeIntel



#  其他补充

<div class="uk-panel uk-panel-box">

# Sublime Text 3打造開發React的環境

* * *

<div class="tm-article-meta"><span>Eddy</span><span><time datetime="2016-01-26">26 一月 2016</time></span><span>標籤</span>: [React](/component/tags/tag/18-react.html), [Sublime Text 3](/component/tags/tag/24-sublime-text-3.html)<span>點擊數</span>: 1090</div>

## 前言

本文是設置Sublime Text 3如何打造一個開發React的環境。主要提供了幾個功能：

*   語法高亮度顯示
*   語法檢查
*   程式片段(Snippets)
*   自動完成代碼

不過缺少了一些功能，例如HTML轉換JSX之類的，目前沒有看到有可以使用的這些外掛。就加減使用了。

> 2016/1/29 加上自動完成套件和(Zen Coding)Emmet支援JSX的說明

## 步驟一：安裝所需的模組

NPM要先安裝，node.js安裝後就有npm了。一共要裝三個模組：

```
npm install -g eslint babel-eslint eslint-plugin-react
```

## 步驟二：安裝Sublime Text 3的外掛

下面這幾套應該一般都會有裝了，沒有就裝上吧：

1.  [Emmet](https://github.com/sergeche/emmet-sublime#readme)
2.  [SublimeCodeIntel](https://github.com/SublimeCodeIntel/SublimeCodeIntel)
3.  [SublimeLinter](http://sublimelinter.readthedocs.org/en/latest/installation.html?__hstc=256467284.99aa324ebb1e7d2f4c97b1e51986f131.1452323300898.1453645015531.1453647501807.3&__hssc=256467284.1.1453647501807&__hsfp=256155588)

要加裝的有以下幾個：

1.  [SublimeLinter-contrib-eslint](https://github.com/roadhump/SublimeLinter-eslint#plugin-installation)
2.  [babel-sublime](https://github.com/babel/babel-sublime#installation)
3.  [Babel Snippets](https://github.com/babel/babel-sublime-snippets)

兩個設定，一個是高亮度顯示，另一個是減少其他的外掛衝突到：

*   Color Scheme: Preferences -> Color Scheme -> Babel
*   (可選的)在你的Preferences.sublime-settings加上：`"ignored_packages": ["JavaScript"]`

## 步驟三：設定 ESLint的設定檔

在專案的根目錄加一個`.eslintrc`檔案，檔案的內容如下：

```
{
  // use babel-eslint for parsing!
  "parser": "babel-eslint",
  "env": {
    // for browser
    "browser": true,
    // in CommonJS
    "node": true
  },
  // some rule options:
  "rules": {
    "quotes": [2, "single"],
    "eol-last": [0],
    "no-mixed-requires": [0],
    "no-underscore-dangle": [0]
  }
}
```

所有的可設定的規則[在這裡](http://eslint.org/docs/rules/)。

## (附加說明)Emmet可以支援JSX

現在Emmet已經可以直接支援JSX。在js或jsx檔案中，用`control+e`展開。

影片：[Emmet expansions and className in React JSX](http://wesbos.com/emmet-react-jsx-sublime/)

## (可選的)步驟：關閉jshint

如果你也有安裝sublime-jshint(SublimeLinter的外掛)，記得要關閉它。關閉它的方法是打開專案的`.sublime-project`檔案，加上以下的設定值：

```
{

    "SublimeLinter":{
        "linters":{
            "eslint":{
                "excludes":[
                    "dist/*",
                    "node_modules/*"
                ]
            },
            "jshint":{
                "@disable":true
            }
        }
    }
}
```

## 步驟四：重開Sublime Text 3(ST3)

最後要重開ST3，才能讓剛作的所有設定正常運作。

## 參考資料

*   [Linting React/JSX and ES6 Javascript with Eslint in Sublime Text 3](http://cheng.logdown.com/posts/2015/09/15/linting-react-jsx-and-es6-javascript-with-eslint)
*   [Lint Like It’s 2015](https://medium.com/@dan_abramov/lint-like-it-s-2015-6987d44c5b48#.e9gzq5f9r)
*   [Set up Sublime Text for Meteor ES6 (ES2015) and JSX Syntax and Linting](http://info.meteor.com/blog/set-up-sublime-text-for-meteor-es6-es2015-and-jsx-syntax-and-linting)
*   [How to Configure Text Editors and IDEs for React.js](https://github.com/kriasoft/react-starter-kit/blob/master/docs/how-to-configure-text-editors.md)
*   [Emmet expansions and className in React JSX](http://wesbos.com/emmet-react-jsx-sublime/)

<div id="fb-root" class=" fb_reset">

<div style="position: absolute; top: -10000px; height: 0px; width: 0px;">

<div><iframe name="fb_xdm_frame_http" frameborder="0" allowtransparency="true" allowfullscreen="true" scrolling="no" id="fb_xdm_frame_http" aria-hidden="true" title="Facebook Cross Domain Communication Frame" tabindex="-1" src="http://staticxx.facebook.com/connect/xd_arbiter.php?version=42#channel=f3404739e8c2ebc&amp;origin=http%3A%2F%2Feddychang.me" style="border: none;"></iframe><iframe name="fb_xdm_frame_https" frameborder="0" allowtransparency="true" allowfullscreen="true" scrolling="no" id="fb_xdm_frame_https" aria-hidden="true" title="Facebook Cross Domain Communication Frame" tabindex="-1" src="https://staticxx.facebook.com/connect/xd_arbiter.php?version=42#channel=f3404739e8c2ebc&amp;origin=http%3A%2F%2Feddychang.me" style="border: none;"></iframe></div>

</div>

</div>

<script>(function(d, s, id) { var js, fjs = d.getElementsByTagName(s)[0]; if (d.getElementById(id)) return; js = d.createElement(s); js.id = id; js.src = '//connect.facebook.net/zh_TW/all.js#xfbml=1&appId=441411672723522'; fjs.parentNode.insertBefore(js, fjs); }(document, 'script', 'facebook-jssdk'));</script>

<div class="fb-comments fb_iframe_widget fb_iframe_widget_fluid" data-width="100%" data-href="http://eddychang.me/blog/16-javascript/51-sublime-text-3-react.html" data-num-posts="10" fb-xfbml-state="rendered"><span style="height: 185px;"><iframe id="f3a0bf52f947934" name="f37c52b163104bc" scrolling="no" title="Facebook Social Plugin" class="fb_ltr fb_iframe_widget_lift" src="https://www.facebook.com/plugins/comments.php?api_key=441411672723522&amp;channel_url=http%3A%2F%2Fstaticxx.facebook.com%2Fconnect%2Fxd_arbiter.php%3Fversion%3D42%23cb%3Df342428b98baaac%26domain%3Deddychang.me%26origin%3Dhttp%253A%252F%252Feddychang.me%252Ff3404739e8c2ebc%26relation%3Dparent.parent&amp;href=http%3A%2F%2Feddychang.me%2Fblog%2F16-javascript%2F51-sublime-text-3-react.html&amp;locale=zh_TW&amp;numposts=10&amp;sdk=joey&amp;width=100%25" style="border: none; overflow: hidden; height: 185px; width: 100%;"></iframe></span></div>

</div>



#   另
<div class="container mt30">

<div class="row">

<div class="col-xs-12 col-md-9 main ">

<div class="article fmt article__content" data-id="1190000003954626">

# 编辑器选择

最近在学习ReactJS，这东西确实不错，但是在实际开发中却有很多问题。不是ReactJS本身的问题，而是开发环境，目前而言并没发现一个真正完美支持JSX语法的编辑器或IDE，这对于ReactJS开发者来说无疑是一个很头疼的事情，以往所习惯的码字方式都要改变，基本上要纯手打，虽然纯手打可以帮助记忆代码，但在工作效率上却就会大打折扣。

## HBuilder

之前一直用的是DCloud研发的[Hbuilder](http://www.dcloud.io/)来做WEB开发，可能很多人都不熟悉这个工具，简单说就是一个国产的WEB开发专用的IDE，集成了很多功能，习惯了之后工作效率确实提升不少。但Hbuilder在第三方插件方面比较弱，ReactJS的相关插件一个都没有，于是我只能换编辑器了。

## Atom

现在的编辑器也很多，这里就不一一列举了。就目前我了解的来说，支持JSX语法高亮、代码提示以及代码校验的插件不多。Atom上有一个比较完善的ReactJS插件[ATOM REACT](http://orktes.github.io/atom-react/)，试用了一下，确实功能挺多，让我小激动了一下。但是Atom的性能却让我很不爽，首先是内存占用太大，我用的OSX，内存一下飙到900M+，一个IDE都没这么占内存。其次就是编辑较大的文件就会卡顿，那敲代码的延迟感简直不能忍，于是我放弃了Atom，可惜了这么好的一个插件。

## SublimeText

这个编辑器就不多说明了，做WEB开发的多少都了解一些，我之前用过一段时间的SublimeText，觉得找插件很麻烦，就投靠了可以一次搞定的HBuilder。现在重新启用了这个神器，因为我找到了几个很棒的ReactJS插件，下面就来具体说说。

# SublimeText插件

做ReactJS开发最需要的无疑是这两条：语法高亮、代码提示，如果能够想Emmet那样自动扩展就更好了，这里我可以告诉你，确实可以实现。

## 语法高亮

[Babel-Sublime](https://github.com/babel/babel-sublime)插件很好的支持了JSX语法的高亮显示，连包裹在组件中的HTML标签都能实现高亮显示，具体的插件安装以及设置方法就不多说了，自行看GitHub上的介绍吧，很简单。

## 代码提示

[Sublime-React](https://github.com/reactjs/sublime-react)插件严格的说并不是一个代码提示插件，而是一个类似于Emmet的自动扩展代码插件，只需要简单敲几个字母然后按下**TAB**键就能自动扩展成你想要的完整代码片段，效果如下图所示。

![](/img/bVqKRI)

<pre>

<div class="widget-codetool" style="display: none;"><button class="selectCode btn btn-xs">全选</button><button href="javascript:void(0);" class="copyCode btn btn-xs" data-clipboard-text="//支持的代码片段如下
cdm→  componentDidMount: fn() { ... }
cdup→  componentDidUpdate: fn(pp, ps) { ... }
cs→  var cx = React.addons.classSet;
cwm→  componentWillMount: fn() { ... }
cwr→  componentWillReceiveProps: fn(np) { ... }
cwu→  componentWillUpdate: fn(np, ns) { ... }
cwun→  componentWillUnmount: fn() { ... }
cx→  cx({ ... })
fdn→  React.findDOMNode(...)
fup→  forceUpdate(...)
gdp→  getDefaultProps: fn() { return {...} } 
gis→  getInitialState: fn() { return {...} } 
ism→  isMounted()
props→  this.props.
pt→  propTypes { ... }
rcc→  component skeleton
refs→  this.refs.
ren→  render: fn() { return ... }
scu→  shouldComponentUpdate: fn(np, ns) { ... }
sst→  this.setState({ ... })
state→  this.state." data-toggle="tooltip" data-placement="bottom" title="">复制</button><button href="javascript:void(0);" class="saveToNote btn btn-xs">放进笔记</button></div>

`<span class="hljs-comment">//支持的代码片段如下</span>
cdm→  componentDidMount: fn() { ... }
cdup→  componentDidUpdate: fn(pp, ps) { ... }
cs→  <span class="hljs-keyword">var</span> cx = React.addons.classSet;
cwm→  componentWillMount: fn() { ... }
cwr→  componentWillReceiveProps: fn(np) { ... }
cwu→  componentWillUpdate: fn(np, ns) { ... }
cwun→  componentWillUnmount: fn() { ... }
cx→  cx({ ... })
fdn→  React.findDOMNode(...)
fup→  forceUpdate(...)
gdp→  getDefaultProps: fn() { <span class="hljs-keyword">return</span> {...} } 
gis→  getInitialState: fn() { <span class="hljs-keyword">return</span> {...} } 
ism→  isMounted()
props→  <span class="hljs-keyword">this</span>.props.
pt→  propTypes { ... }
rcc→  component skeleton
refs→  <span class="hljs-keyword">this</span>.refs.
ren→  render: fn() { <span class="hljs-keyword">return</span> ... }
scu→  shouldComponentUpdate: fn(np, ns) { ... }
sst→  <span class="hljs-keyword">this</span>.setState({ ... })
state→  <span class="hljs-keyword">this</span>.state.`</pre>

## JSX中使用Emmet

虽然上面这个插件可以实现JSX的代码扩展，但是在JSX中包裹的HTML却不能直接支持Emmet，需要通过安装其他插件以及修改相应设置来实现。
首先是安装需要的插件：**RegReplace**和**Chain Of Command**，直接在插件库中搜索安装即可。
接下来就是设置了，先在`KeyBinding – Users`中插入下面这段代码：

<pre class="hljs json">

<div class="widget-codetool" style="display: none;"><button class="selectCode btn btn-xs">全选</button><button href="javascript:void(0);" class="copyCode btn btn-xs" data-clipboard-text="  {
    &quot;keys&quot;: [&quot;tab&quot;],
    &quot;command&quot;: &quot;expand_abbreviation_by_tab&quot;, 
    &quot;context&quot;: [{
        &quot;operand&quot;: &quot;source.js&quot;, 
        &quot;operator&quot;: &quot;equal&quot;, 
        &quot;match_all&quot;: true, 
        &quot;key&quot;: &quot;selector&quot;
    },{
        &quot;key&quot;: &quot;preceding_text&quot;, 
        &quot;operator&quot;: &quot;regex_contains&quot;, 
        &quot;operand&quot;: &quot;(\\b(a\\b|div|span|p\\b|button)(\\.\\w*|>\\w*)?)&quot;, 
        &quot;match_all&quot;: true
    },{
        &quot;key&quot;: &quot;selection_empty&quot;, 
        &quot;operator&quot;: &quot;equal&quot;, 
        &quot;operand&quot;: true, 
        &quot;match_all&quot;: true
    }]
  }" data-toggle="tooltip" data-placement="bottom" title="">复制</button><button href="javascript:void(0);" class="saveToNote btn btn-xs">放进笔记</button></div>

 `{
    "<span class="hljs-attribute">keys</span>": <span class="hljs-value">[<span class="hljs-string">"tab"</span>]</span>,
    "<span class="hljs-attribute">command</span>": <span class="hljs-value"><span class="hljs-string">"expand_abbreviation_by_tab"</span></span>, 
    "<span class="hljs-attribute">context</span>": <span class="hljs-value">[{
        "<span class="hljs-attribute">operand</span>": <span class="hljs-value"><span class="hljs-string">"source.js"</span></span>, 
        "<span class="hljs-attribute">operator</span>": <span class="hljs-value"><span class="hljs-string">"equal"</span></span>, 
        "<span class="hljs-attribute">match_all</span>": <span class="hljs-value"><span class="hljs-literal">true</span></span>, 
        "<span class="hljs-attribute">key</span>": <span class="hljs-value"><span class="hljs-string">"selector"</span></span> },{
        "<span class="hljs-attribute">key</span>": <span class="hljs-value"><span class="hljs-string">"preceding_text"</span></span>, 
        "<span class="hljs-attribute">operator</span>": <span class="hljs-value"><span class="hljs-string">"regex_contains"</span></span>, 
        "<span class="hljs-attribute">operand</span>": <span class="hljs-value"><span class="hljs-string">"(\\b(a\\b|div|span|p\\b|button)(\\.\\w*|>\\w*)?)"</span></span>, 
        "<span class="hljs-attribute">match_all</span>": <span class="hljs-value"><span class="hljs-literal">true</span></span> },{
        "<span class="hljs-attribute">key</span>": <span class="hljs-value"><span class="hljs-string">"selection_empty"</span></span>, 
        "<span class="hljs-attribute">operator</span>": <span class="hljs-value"><span class="hljs-string">"equal"</span></span>, 
        "<span class="hljs-attribute">operand</span>": <span class="hljs-value"><span class="hljs-literal">true</span></span>, 
        "<span class="hljs-attribute">match_all</span>": <span class="hljs-value"><span class="hljs-literal">true</span></span> }]</span> }`</pre>

这样就实现了在JSX中按**TAB**键来扩展HTML片段了，但是JSX中的HTML和标准的HTML又有不同的地方，就是HTML中的`class`，在JSX中是`className`，所以这里就需要修改**RegReplace**的设置，找到Packagea Setting --> Reg Replace --> Settings-User，插入下面这段代码：

<pre class="hljs json">

<div class="widget-codetool" style="display:none;"><button class="selectCode btn btn-xs">全选</button><button href="javascript:void(0);" class="copyCode btn btn-xs" data-clipboard-text="{
    &quot;replacements&quot;: {
        &quot;js_class&quot;: {
            &quot;find&quot;: &quot; class=\&quot;&quot;,
            &quot;replace&quot;: &quot; className=\&quot;&quot;,
            &quot;greedy&quot;: true,
            &quot;case&quot;: false
        }
    }
}" data-toggle="tooltip" data-placement="bottom" title="">复制</button><button href="javascript:void(0);" class="saveToNote btn btn-xs">放进笔记</button></div>

`{
    "<span class="hljs-attribute">replacements</span>": <span class="hljs-value">{
        "<span class="hljs-attribute">js_class</span>": <span class="hljs-value">{
            "<span class="hljs-attribute">find</span>": <span class="hljs-value"><span class="hljs-string">" class=\""</span></span>,
            "<span class="hljs-attribute">replace</span>": <span class="hljs-value"><span class="hljs-string">" className=\""</span></span>,
            "<span class="hljs-attribute">greedy</span>": <span class="hljs-value"><span class="hljs-literal">true</span></span>,
            "<span class="hljs-attribute">case</span>": <span class="hljs-value"><span class="hljs-literal">false</span></span> }</span> }</span> }`</pre>

这样就大功告成了，开始快乐的学习ReactJS吧~~！欢迎各位大神来补充。

</div>

</div>

</div>

</div>

</div>

</div>

</div>
