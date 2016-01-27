title: 认识 scrat
speaker: 吴荣华(rahul.wu)
url: https://github.com/wurh/mynodeppt
transition: slide3
files: /js/demo.js,/css/demo.css,/js/zoom.js
theme: dark
usemathjax: yes

[slide]
# 首先？

[slide]
# 来个自我介绍吧
----
* 我叫吴荣华 {:&.rollIn}
* 目前负责前端业务
* github地址:https://github.com/wurh
* 欢迎大家访问上面的地址，然后点击follow

[slide]
## 防伪图片
![rahul](/img/myself.png "rahul")

[slide]
#进入正题

[slide]
#why scrat?

[slide]
----
* 我们希望能像 搭积木 一样开发和维护系统，最终通过 组装模块 得到一个完整的应用。

[slide]
#模块化开发！！！

[slide]
* 在模块化系统的结构中，模块是可组合、可分解和更换的单元，这就要求模块本身具有一定的 独立性，完整的前端模块化方案需要将js、css和模板维护在一起，保证模块的独立
![rahul](/img/mokuai1.png "rahul")

[slide]
模块
----
* 一个模块一个目录 {:&.rollIn}
* 像写node.js 一样写模块
* 将模板嵌入到js中使用

[slide]
![rahul](/img/mokuai2.png "rahul")

[slide]
----
* “我们希望每次研发新产品不是从零开始，不同团队不同项目之间能有可复用的模块沉淀下来。”

[slide]
![rahul](/img/tree.png "rahul")

[slide]
#组件生态!!!
----
* 每个项目有工程模块和生态模块 {:&.rollIn}
* 生态模块基于 component 规范开发，部署到Github上
* 可以通过命令行工具将Github上的模块安装到工程中使用



[slide]
<iframe data-src="http://scrat.io/#!/index" src="about:blank;" style="width:1000px;height:600px"></iframe>

