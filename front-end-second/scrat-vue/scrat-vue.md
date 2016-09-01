title: scrat + vue 快速搭建组件式架构
speaker: 吴荣华(rahul.wu)
url: https://github.com/wurh/mynodeppt
transition: zoomout
theme: light
highlightStyle: monokai_sublime
usemathjax: yes

[slide data-transition="zoomout"]
# scrat + vue 快速搭建组件式架构

[slide data-transition="zoomout"]
# 首先？

[slide data-transition="zoomout"]
# 来个自我介绍吧
----
* 我叫吴荣华 {:&.rollIn}
* 目前负责出口事业部<span style="color:orange">前端业务</span>
* github地址:https://github.com/wurh
* 欢迎大家访问上面的地址，然后点击<span style="color:#00ff00">follow</span>

[slide data-transition="zoomout"]
## 防伪图片
![rahul](/img/myself.png "rahul")

[slide data-transition="zoomout"]
# 进入正题


[slide data-transition="zoomout"]
----
# 项目背景

- VIPME 业务快速增长迭代，需要多个业务平台进行支撑
- 公司各系统接入需要多方配合支撑，周期较长
- 10个人左右的前端工程师队伍
- 支撑8+个业务 -- 繁，杂
- 众多专题，活动项目

[slide data-transition="zoomout"]
#需求

- 需要搭建可复用组件的架构
- 需要搭建已经包含工程化(代码压缩，合并；combo服务，实施监听代码变化等)的架构
- 需要灵活套用各种UI框架，提高平台逼格的架构

[slide data-transition="zoomout"]

#选型

- scrat 完成模块化，工程化实现
- vue 实现组件化，模板开发

[slide data-transition="zoomout"]

# 认识 scrat

- scrat 是一个模块化的开发框架

[slide data-transition="zoomout"]

官网地址：http://scrat.io/#!/index

![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/scrat.png "概念图")

[slide data-transition="zoomout"]

# 特点如下:

- 一个目录一个模块，模块包含（模板文件，脚本，样式，以及静态资源）
- 支持模块化开发，模块间引入与nodejs保持一致
- 支持css预处理， stylus less sass 等
- 与nodejs服务框架（express） 完美配合，可进行前后端服务层面分离

[slide data-transition="zoomout"]
# 认识 Vue
- Vue 是一个实现了web component 式开发的轻量级mvvm框架

# 官网地址：http://cn.vuejs.org/
[slide data-transition="zoomout"]
![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/vue1.png "ViewModel")
- 支持数据驱动的视图，实现DOM 与 底层数据 双向绑定

[slide data-transition="zoomout"]
![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/vue2.png "组件式系统")

- 支持把每个界面都可以抽象成多个组件树，多个组件可构建成大型的应用

[slide data-transition="zoomout"]

# scrat + vue 会怎样?

[slide data-transition="zoomout"]

# 比方说是这样的...

[slide data-transition="zoomout"]

![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/scrat-vue.png "合并")

[slide data-transition="zoomout"]
# 实际上是这样的:

[slide data-transition="zoomout"]
# 工程目录:

![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/project3.png "工程目录")

[slide data-transition="zoomout"]

#整个工程基本会由4个目录组成：

- components_modules: 公用组件库 （组件生态,外部引用）
- components：  项目可复用的组件块
- server: node.js 服务层
- views: 工程视图区间以及第三方引用包

[slide data-transition="zoomout"]
# 工程模块间调用设计

![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/des4.png "组件依赖")

[slide data-transition="zoomout"]

# boot.js 作为工程入口配置，负责管理工程路由转发,配置引用等

```javascript
'use strict';

var router = require('router');  //scrat 路由组件
var config = require('../config/n-config.js');
var pages = require('../config/p-config.js');

//----- 路由中间件 -----

// 页面转发加载
var currentPage;
function loadPage(ctx, next) {
    var rootPage;
    var page = ctx.params.page;
    if ('/' + ctx.params.page !== ctx.path) {
        rootPage = ctx.path.split('/' + page)[0].split('/')[1];
    }
    var prectx = ctx;
    if (rootPage) {
        require.async(pages[rootPage], function (p) {
            if (currentPage && currentPage.destory) currentPage.destory(ctx);
            currentPage = p;
            var parentcom;
            if (currentPage.init) {
                parentcom = currentPage.init(ctx);
            }
            var renpage = page;
            parentcom.$broadcast('navi-update', renpage, prectx.params.router);
            runPage(prectx, next, page);
        });
    } else {
        runPage(ctx, next, page)
    }
}

/**
 * 渲染页面
 * @param ctx
 * @param next
 * @param page
 */
function runPage(ctx, next, page) {
    if (pages.hasOwnProperty(page)) {
        require.async(pages[page], function (p) {
            if (currentPage && currentPage.destory) currentPage.destory(ctx);
            currentPage = p;
            if (currentPage.init) currentPage.init(ctx);
        });
    } else {
        next();
    }
}

//----- 页面路由 -----

router('/:page', function (ctx, next) {
    sessionStorage.setItem('excess', 'page');
    next()
},  loadPage);

router('/', function (ctx, next) {
    ctx.params.page = 'index';
    next();
}, loadPage);


router('*', function (ctx) {
    router.replace('/' + config.default);
});

module.exports = function () {
    router.start();
}

```

[slide data-transition="zoomout"]
- config 作为工程前端配置目录，分别有a-config.js; p-config.js; m-config.js

[slide data-transition="zoomout"]
# a-config.js  负责API接口配置管理

``` js
'use strict';

/**
 * api config
 * @type {{}}
 */


var host = '';

// 请求类型
var ajaxType = {
    get: 'GET',
    post: 'POST'
}

// 请求路径
var path = {
	'login' : '/api/login'
}


// 返回码配置
var code = {
    common: {
        succ: 200,
        miss: 1001
    }
}

module.exports = {
    ajaxType: ajaxType,
    path: path,
    code: code
}
```

[slide data-transition="zoomout"]

# p-config.js 负责页面指向配置管理
``` js
'use strict'

/**
 * page config
 */
var pageconfig = {
    index:'pages/index',    //首页
    active:'pages/active',   //有效过滤页
    completed:'pages/completed'   //有效过滤页
}
module.exports = pageconfig

```

[slide data-transition="zoomout"]
m-config.js 负责菜单项配置管理
``` js
'use strict';

/**
 *   menu config
 */
module.exports = {
    default: 'index', //配置默认显示页面
    defaultClass: 'fadeOutLeft animated',//默认样式
    menu: [
    ]
};

```

[slide data-transition="zoomout"]
- util目录为全工程通用工具包
- common目录为全工程通用业务包

[slide data-transition="zoomout"]
- page 目录为页面组件
- index 页面:index 目录下会存放 index.js;index.tpl;index.styl

[slide data-transition="zoomout"]
# index 页面代码
``` js
'use strict';

var tpl = __inline('index.tpl');
var head = require('widgets/head');
var list =  require('widgets/list');
var footer = require('widgets/footer');

/**
 * 首页模块
 *
 * @class index
 * @constructor
 */
var index = Vue.extend({
    template: tpl,
    components: {
        "c-head": head(),
        "c-list" : list(),
        "c-footer":footer()
    },
    ready:function () {
        this.$broadcast('onUpdateVis','all');
    },
    events: {
        'onAddTodo': function (value) {
           this.$broadcast('onAddListItem',value);
        }
    }
});

/**
 * My method description.  Like other pieces of your comment blocks,
 * this can span multiple lines.
 *
 * @method init
 * @return {Object} Returns index page component
 */
var init = function () {
    return new index({
        el: "#page-main",
        replace: false
    })
}

module.exports = {
    init: init
}

```
[slide data-transition="zoomout"]
- widgets 目录为可复用独立组件

[slide data-transition="zoomout"]
- 举个栗子head组件， head 组件目录同样会存在head.js, head.tpl, head.styl文件

[slide data-transition="zoomout"]
# head 组件代码块
``` js
'use strict';

/**
 * 头部组件
 *
 * @class head
 * @constructor
 */

var tpl = __inline('head.tpl');
var head = Vue.extend({
    template: tpl,
    ready: function () {
        return {
            value:''
        }
    },
    props: ['page'],
    methods: {
        addTodo: function () {
            var value = this.newTodo && this.newTodo.trim();
            if (!value) {
                return;
            }
            this.$dispatch('onAddTodo',value);
            this.newTodo = '';
        },
    },
    replace: false
});


/**
 * My method description.  Like other pieces of your comment blocks,
 * this can span multiple lines.
 *
 * @method init
 * @return {Object} Returns head component
 */
var init = function () {
    return head;
}

module.exports = init;
```

[slide data-transition="zoomout"]
# 因此一个页面的划分与组成这样的:

[slide data-transition="zoomout"]
# 原来：
![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/ori.png "原来的样子")

[slide data-transition="zoomout"]
# 划分：
![alt text](http://7xawfk.com1.z0.glb.clouddn.com/blog/todom1.png "原来的样子")

[slide data-transition="zoomout"]
# 总结:
- 当模块化的框架工程遇到组件式的框架技术，将会产生提高前端研发效率的火花!

[slide data-transition="zoomout"]
# Q&A
## 谢谢大家 -- O(∩_∩)O！


