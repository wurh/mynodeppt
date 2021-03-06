title: 认识 scrat
speaker: 吴荣华(rahul.wu)
url: https://github.com/wurh/mynodeppt
transition: slide3
files: /js/demo.js,/css/demo.css,/js/zoom.js
theme: dark
usemathjax: yes

[slide data-transition="horizontal3d"]
# scrat 与 活动运营

[slide data-transition="horizontal3d"]
# 首先？

[slide data-transition="horizontal3d"]
# 来个自我介绍吧
----
* 我叫吴荣华 {:&.rollIn}
* 目前负责出口事业部<span style="color:orange">前端业务</span>
* github地址:https://github.com/wurh
* 欢迎大家访问上面的地址，然后点击<span style="color:#00ff00">follow</span>

[slide data-transition="horizontal3d"]
## 防伪图片
![rahul](/img/myself.png "rahul")

[slide data-transition="horizontal3d"]
#进入正题

[slide data-transition="horizontal3d"]
#why scrat?

[slide data-transition="horizontal3d"]
----
* 我们希望能像 搭积木 一样开发和维护系统;
* 最终通过 组装模块 得到一个完整的应用。


[slide data-transition="horizontal3d"]
#模块化开发！！！

[slide data-transition="horizontal3d"]
* 在模块化系统的结构中，模块是可组合、可分解和更换的单元，这就要求模块本身具有一定的 独立性，完整的前端模块化方案需要将js、css和模板维护在一起，保证模块的独立
![rahul](/img/mokuai1.png "rahul")

[slide data-transition="horizontal3d"]
模块
----
* 一个模块一个目录 {:&.rollIn}
* 像写node.js 一样写模块
* 将模板嵌入到js中使用

[slide data-transition="horizontal3d"]
![rahul](/img/mokuai2.png "rahul")

[slide data-transition="horizontal3d"]
----
* 希望每次研发新产品不是从零开始;
* 不同团队不同项目之间能有可复用的模块沉淀下来。
* 本月甚至本周要上线30个活动专题页

[slide data-transition="horizontal3d"]
![rahul](/img/tree.png "rahul")


[slide data-transition="horizontal3d"]
#组件生态!!!
----
* 每个项目有工程模块和生态模块 {:&.rollIn}
* 生态模块基于 component 规范开发，部署到Github上
* 可以通过命令行工具将Github上的模块安装到工程中使用

[slide data-transition="horizontal3d"]
#因此我们选择了scrat！

[slide data-transition="horizontal3d"]
#未来?

[slide data-transition="horizontal3d"]
#模块化活动运营之路~  (计划)

[slide data-transition="horizontal3d"]
#活动运营后台

[slide data-transition="horizontal3d"]
#前端个性化
----
* 希望能区分用户群体,内容差异化,个性化 {:&.rollIn}
* 页面可以分模板，分模块
* 按一定条件组件对应的运营页，支持灰度与定时发布
* 高性能要求

[slide data-transition="horizontal3d"]
![rahul](/img/yunyinghoutai.png "rahul")

[slide data-transition="horizontal3d"]
#But...
----
* 数据模板耦合，运营直接改代码? {:&.rollIn}
* 只支持html 模块管理，脚本样式如何管理?
* 页面个性化，模板随便冗余，如何进行版本管理?
* 条件分支多，调试，测试，定位困难...

[slide data-transition="horizontal3d"]
#So
----
##开发阶段
* 定义好代码的组织 {:&.rollIn}
* 代码的规范化
* 做好页面组件划分

[slide data-transition="horizontal3d"]
##上线阶段
----
* 组件重用性 {:&.rollIn}
* 组件的丰富性

[slide data-transition="horizontal3d"]
##运营阶段
----
* 理解统一 {:&.rollIn}
* 技术隔离
* 可视化与傻瓜式运营

[slide data-transition="horizontal3d"]
![rahul](/img/huodongpc1.png "rahul")

[slide data-transition="horizontal3d"]
![rahul](/img/huodongwap.png "rahul")

[slide data-transition="horizontal3d"]
#结论:
----
* 页面 = 布局 + 组件 {:&.rollIn}
* 组件 = 模板 + 样式 + 脚本 + 图片 + 数据


[slide data-transition="horizontal3d"]
## 通过scrat olpm 模式打通前端工程链路

[slide data-transition="horizontal3d"]
## 通过线上数据运营管理后台
----
* 完成可视化傻瓜式运营 {:&.rollIn}
* (计划中~~)

[slide data-transition="horizontal3d"]
## 演示

[slide data-transition="horizontal3d"]
# Q&A
## 谢谢大家 -- O(∩_∩)O！


