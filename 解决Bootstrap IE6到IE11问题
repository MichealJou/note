让IE6 IE7 IE8 IE9 IE10 IE11支持Bootstrap的解决方法

最近做一个Web网站，之前一直觉得bootstrap非常好，这次使用了bootstrap3,在chrome,firefox,safari,opera，360浏览器（极速模式）、搜狗浏览器等浏览器下均没有问题，而在IE8及IE11下发现样式无法显示，然后各种百度啊，最后在 雅朋网 的一个网友帖子的帮助下解决了问题，也参考了 千寻学习网 的资料，先将解决方法总结如下：


首先需要确保你的HTML页面开始部分要有DOCTYPE声明。DOCTYPE告诉浏览器使用什么样的HTML或XHTML规范来解析HTML文档，具体会影响：
对标记attributes 、properties的约束规则
对浏览器的渲染模式产生影响，不同的渲染模式会影响到浏览器对于CSS代码甚至JavaScript脚本的解析
DOCTYPE是非常关键的，目前的最佳实践就是在HTML文档的首行键入：
<!DOCTYPE html>


大神的帖子总结的bootstrap的查找原因好几条，首先，Bootstrap3 是移动设备优先的原则开发的，所以原因可能如下：
1.没有正确调用远程地址
即只要是IE9以下，就调用两个专门的js
<!-- HTML5 Shim and Respond.js IE8 support of HTML5 elements and media queries -->
<!--[if lt IE 9]>
  <script src="http://apps.bdimg.com/libs/html5shiv/3.7/html5shiv.min.js"></script>
  <script src="http://apps.bdimg.com/libs/respond.js/1.4.2/respond.min.js"></script>
<![endif]-->
但是我测试发现仅仅使用以上js文件不可行，
2.调用方法不正确
不要用file://或@import形式引用respond.min.js或respond.js或css文件


3.针对浏览器的内容做标识（使用meta标签调节浏览器的渲染方式）
bootstrap不支持IE兼容模式，为了让IE浏览器运行最新的渲染模式，将添加以下标签在页面中
<meta http-equiv="X-UA-Compatible" content="IE=edge,Chrome=1" />
IE=edge表示强制使用IE最新内核，chrome=1表示如果安装了针对IE6/7/8等版本的浏览器插件Google Chrome Frame（可以让用户的浏览器外观依然是IE的菜单和界面，但用户在浏览网页时，实际上使用的是Chrome浏览器内核），那么就用Chrome内核来渲染。关于此meta标签的具体说明，可参见StackOverflow上的精彩回答，<meta>标签高人的英文解释可以参看
http://stackoverflow.com/questions/6771258/whats-the-difference-if-meta-http-equiv-x-ua-compatible-content-ie-edge-e
我有加了一句
<meta http-equiv="X-UA-Compatible" content="IE=9" />
然后就可以了
内核控制Meta标签，因为目前国内的主流浏览器都是双内核，故而添加meta标签来告诉浏览器使用什么内核来渲染页面


4.IE8不支持container的几个属性
IE8不完全支持box-sizing:border-box与min-width, max-width, min-height或max-height的一起使用.所以，v3.0.1的bootstrap中对container的类，已经不再使用max-width了。


5.JS与CSS的引入顺序导致的问题
必须先引用css在引用js
<link rel="stylesheet" type="text/css" href="bootstrap.min.css" media="screen"/>
<script type="text/javascript" src="js/respond.min.js"></script>


6.DOCTYPE前后有空行
<!DOCTYPE html>
这里有空格也不行，要去掉空格
<html>


7.也可以手动修改bootstrap.css
如果您使用的是bootstrap2.1.1，修改了navbar-inner{ filter:none}可解决问题，如果使用的是3.0+版的，没有这段代码了，详细介绍请看连接
http://stackoverflow.com/questions/12460190/bootstrap-navbar-does-not-show-in-ie8


8.使用quirks mode（兼容模式）
定义网页时，向后兼容旧的浏览器的模式就是quirks mode，与之对应的是“标准模式”就是 standard mode。具体是将<!DOCTYPE html>写成以前的这种
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
这个我测试过，不可行


最后我在IE11下测试通过，但是在IE8下测试，有发现一个问题placeholder不被支持
下面是解决IE支持placeholder的方法
本文引用的jquery是1.11.1测试通过，先引用jquery
<script type="text/javascript" src="http://code.jquery.com/jquery-1.11.1.min.js"></script>
也可以用其他的jquery版本
再引入<script type="text/javascript" src="js/jquery.placeholder.js"></script>
jquery.placeholder.js这个文件的下载地址https://github.com/mathiasbynens/jquery-placeholder
然后再文件中加入一下代码
<script type="text/javascript">
    $(function () {
        // Invoke the plugin
        $('input, textarea').placeholder();
    });
</script>
如果我这里为涉及到的或者问题依然没有解决的请移步http://hustlzp.com/post/2014/01/ie8-compatibility更加详细


以上IE6,7,8,9,10,11,chrome,firefox,safari,opera，360浏览器（极速模式）、搜狗浏览器测试通过，只有IE5.5似乎不太可行，总之问题解决到此，万恶的IE6-都叫它打酱油去吧


如果您不想使用jquery.placeholder.js,再不支持placeholder的浏览器下模拟placeholder实现
可参考此文讲很详细http://ju.outofmemory.cn/entry/1595
