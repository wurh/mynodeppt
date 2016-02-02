title: 大前端之PC篇 
speaker: 吕健伟
theme: green
url: https://github.com/ksky521/nodePPT
transition: zoomin

[slide]
# 大前端之PC篇 
## 出口事业部 - 前端组 - 吕健伟

[slide]
## 分享主题
- PC浏览器的发展现状 {:&.fadeIn}
- PC端前端 - 过去，现在，未来

[slide]
<img src="/images/2016-02-01/browser-version.png" />
- 考虑兼容浏览器：chrome, firefox5+, Safari7+, IE8+

[slide]
## 前端工程师永远的痛 - IE浏览器
-------------
<img src="/images/2016-02-01/ie.jpg" />

[slide]
##面对IE浏览器，想用上html5, css3？
-------------
- 兼容性（需考虑低版本IE浏览器，实现成本大）
- 页面性能（过多的动画效果会导致性能下降）

[slide]
## PC端前端似乎能做的事情不多
-------------
- 页面重构
- 实现中规中矩的交互
- 除了实现业务需求，还是实现业务需求，然后还是实现业务需求
-------------
 ## 但真的是这样么？

[slide]
# PC端前端 - 过去

[slide]
## 页面重构
-------------
- PSD切图 {:&.fadeIn}
- 使用html，css构造兼容性良好的页面
- 简称“切图仔”

[slide]
## 交互实现
-------------
- 实现兼容性、性能良好的交互 {:&.fadeIn}
- 使用Ajax技术请求接口数据进行展示
- 简称“js工程师”

[slide]
## 这就够了么？ 
-------------
- 重复繁琐的工作内容 {:&.fadeIn}
- 技术门槛低，基本没有核心竞争力
- 对业务不了解
- 处于手工作坊年代

[slide]
# PC端前端 - 现在

[slide]
## 前端模块化
-------------
- 抽取公共样式 - UI框架 {:&.fadeIn}
- 抽取交互组件 - JS组件
- 使用MVC，MVVM框架 - 成熟的开发模式

[slide]
## 理解业务 -> 分析需求
-------------
<img src="/images/2016-02-01/component.png" />

[slide]
<style>
	#page-component {width: 730px; margin: 0 auto;}
	#page-component img {float: left; margin-right: 40px;}
</style>
## 实现需求 
-------------
<div id="page-component">
	<img src="/images/2016-02-01/component-src.png" />
	<img src="/images/2016-02-01/css-src.png" />
	<img src="/images/2016-02-01/js-src.png" />
	<img src="/images/2016-02-01/img-src.png" />
</div>

[slide]
## 初步入门
-------------
- 大幅减少重复的工作内容 {:&.fadeIn}
- 积累相关的经验，具备一定的竞争力
- 理解业务，具备初步的全局观

[slide]
## 这就够了么？
-------------
- 面对庞大的业务系统，代码管理成本上升
- 性能要求（网络流量，页面加载速度）

[slide]
# 前端工程化

[slide]
## 如何实现工程化
-------------
- 使用模块管理类库（require.js，sea.js） {:&.fadeIn}
- 使用工程构建工具（fis，grunt，gulp, webpack）

[slide]
## 模块管理
<pre>
	<code>
var Listeners = require('../component/Listeners/Listeners.js'); // 事件监听
var stringifyJSON = require('../component/StringifyJSON/StringifyJSON'); // JSON序列化
var nsAds = require('./modules/nsAds.js'); // 广告公共请求接口
var adsTpl = require('./tpl/headScroll.ejs'); // 头部走马灯广告模板
var nsCart = require('./modules/nsCart.js'); // mini cart模块
var Time = require('../component/Time/Time.js'); // 倒计时组件
var Selector = require('../component/Selector/Selector.js'); // 下拉组件
var headLoginIn = require('./tpl/head-loginIn.ejs'); // 登陆状态模板
var headLoginOut = require('./tpl/head-loginOut.ejs'); // 未登陆状态模板
var Login = require('./modules/login.js');
var Ajax = require('./modules/ajaxSet.js');
var ga = require('./modules/ga-land.js');
var PlaceHoler = require('../component/jquery.placeholder/placeholder.js');
var cartStorage = require('./modules/setNimCartStorage.js');
	</code>
</pre>

[slide]
## 工程化构建
<pre>
	<code>
gulp.task('build', function () {
    resourceDomain = config.resourceDomain;
    imgDomain = config.imgDomain;
    runSequence('copycon',
                'copyImage', 
                'copydata', 
                'minify',
                'mergeImgCssJSON',
                'uglify',
                'mergeAllJSON');
});
	</code>
</pre>

[slide]
## 能力进阶
-------------
- 能够快速实现业务需求
- 面对庞大的业务系统，保持代码的可维护性
- 满足性能要求（背景图合并，静态资源合并、压缩，静态资源版本管理）
- 岗位：前端工程师

[slide]
## 这样就满足了吗？
-------------
- 前后端捆绑，开发、调试成本高
- 后端接口对前端开发不友好，代码复杂度上升
- 最终的实现不一定是最优解决方案

[slide]
# 大前端时代 - 未来

[slide]
## 什么叫大前端？ 
-------------
- 除了编写客户端代码，还要编写服务端代码 {:&.fadeIn}
- 结合客户端、服务端，以最优的解决方案实现业务需求
- 制作工具、框架、系统，提升实现业务需求的能力

[slide]
## 感谢node.js
-------------
- Node.js是一个基于Chrome JavaScript运行时建立的平台， 用于方便地搭建响应速度快、易于扩展的网络应用。 {:&.bounceIn}
- Node.js 使用事件驱动， 非阻塞I/O 模型而得以轻量和高效，非常适合在分布式设备上运行的数据密集型的实时应用。
- Node是一个Javascript运行环境(runtime)。实际上它是对Google V8引擎进行了封装。V8引 擎执行Javascript的速度非常快，性能非常好。Node对一些特殊用例进行了优化，提供了替代的API，使得V8在非浏览器环境下运行得更好。

[slide]
## 编写服务端代码 - 从梦想走进现实 
-------------
- 将复杂计算迁移到服务端，提升页面性能 {:&.bounceIn}
- 将业务逻辑迁移到服务端，降低客户端代码复杂度，提高代码可重用性
- 向客户端开发提供友好的接口，提升开发速度
- 通过对后端数据接口的模拟，真正实现前后端并行开发

[slide]
## 不是抢后端的饭碗 ~ 
-------------
- 后端可以从复杂多变的业务逻辑抽身 {:&.bounceIn}
- 后端开发可以走向平台化，专注处理高并发，大吞吐量等技术问题

[slide]
## 解析链接路由，渲染模板 - SEO不再蛋疼
-------------
<pre>
	<code>
// 登录页面 
router.get('/login', commonRouter);
router.get('/login', function(req, res, next) {
    var data = {};
    res.render('signin', data);
});

// 注册首页
router.get('/register', commonRouter);
router.get('/register', function(req, res, next) {
    var data = {};
    res.render('register', data);
});
	</code>
</pre>

[slide]
## 模板专注页面呈现 - 更简单，更高的重用性
-------------
<pre>
	<code>
<% if (filter.checkedItem) { %>
    <% if (filter.checkedItem.name) { %>
        <%= filter.checkedItem.name %>
    <% } %>
<% } else { %>
    <%= filter.name %>
<% } %>
<span class="icon-arrow icon-arrow-down"></span>
<span class="icon-arrow icon-arrow-up"></span>
<i class="white-black"></i>
	</code>
</pre>

[slide]
## 测试数据模拟 
-------------
- 读取本地Json文件模拟（目前采用方式）
- <a target="_blank" href="https://github.com/thx/RAP/wiki/home_cn">RAP模拟数据服务</a>（将来采用方式）

[slide]
## 终极目标 
-------------
以模块化、工程化为基础，结合工具及框架，建设可以支撑业务的系统：
- 可以让产品、运营通过操作界面，自动产出符合业务需求的页面
- 前端工程师可以从复杂多变的业务支撑抽身，通过类似搭积木的方式，快速实现业务需求
- 专注技术提升，追求优雅的代码实现及完美的解决方案

[slide]
<img src="/images/2016-02-01/qa.jpg" />

[slide]
<style>
    .thank {corlor: white;}
</style>
<div class="thank">**Thank you!**</div>



