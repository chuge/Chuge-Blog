title: sublime plugins for react
date: 2016-04-09 01:21:15
tags:
---
一些react开发的sublime插件
----------------------
安装sublime插件，按下快捷键 Ctrl+Alt+p 打开Package Control命令面板

### jsformat

js格式化，Ctrl+Alt+F

### Terminal

打开终端并定位到当前目录，Ctrl+shift+T

### babel
支持ES6，React.js, jsx代码高亮，对 JavaScript, jQuery 也有很好的扩展

    *   安装：PC上ctrl+shift+p（MacCmd+shift+p）打开面板输入babel安装

    *   配置：打开.js, .jsx 后缀的文件;

        ```
          打开菜单view，
          Syntax -> Open all with current extension as... -> Babel -> JavaScript (Babel)，
          选择babel为默认 javascript 打开syntax
        ```
### emmet

自动补全标签，输入简写形式，然后按 Tab 键。

React: Ctrl + E
 **修改Emmet兼容jsx 文件(使用Tag 快速完成react 代码书写)**

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

使用super+e触发 emmet；
正则判断用 a，div，span，p，button标签默认tab 触发；


###   [JsFormat](https://github.com/jdc0589/JsFormat) 格式化 js 代码

jsformat 是 sublime 上 js 格式化比较好用的插件之一，通过修改它的`e4x` 属性可以使它支持 jsx。

打开`preferences -> Package Settings -> JsFormat -> Setting - Users`,输入以下代码：

即可保存时自动格式化，并支持 jsx 类型文件.
        ```
      {
        "e4x": true,
        // jsformat options
        "format_on_save": true,
      }
        ```

# SublimeText插件

做ReactJS开发最需要的无疑是这两条：语法高亮、代码提示，如果能够想Emmet那样自动扩展就更好了，这里我可以告诉你，确实可以实现。

## 语法高亮

[Babel-Sublime](https://github.com/babel/babel-sublime)插件很好的支持了JSX语法的高亮显示，连包裹在组件中的HTML标签都能实现高亮显示，具体的插件安装以及设置方法就不多说了，自行看GitHub上的介绍吧，很简单。

## 代码提示

[Sublime-React](https://github.com/reactjs/sublime-react)插件严格的说并不是一个代码提示插件，而是一个类似于Emmet的自动扩展代码插件，只需要简单敲几个字母然后按下**TAB**键就能自动扩展成你想要的完整代码片段，效果如下图所示。


