### 1. ECMA-262标准和W3C标准
- ECMA-262标准  
ECMAScript脚本语言的规范及标准，所有遵循ECMA-262标准实现的脚本都可以称之ECMAScript，如JavaScript。  
*ECMA-262是从ECMAScript脚本引擎实现的角度去描述的。*  

- JavaScript引擎  
即解释器，对JavaScript（动态语言）源代码解析并运行得出结果  

- 编译器
对于C#、Java、C++、C等静态语言，将源代码编译为另一种代码或中间语言（IL等），然后运行结果  

- W3C标准  
万维网联盟发布的一系列标准，针对网页分为三个部分：结构（Structure）、表现（Presentation）和行为（Behavior）  

> 结构标准语言：XML，XHTML  
表现标准语言：css  
行为标准：DOM，ECMAScript

- 常说的js包含两方面的知识：  
js基础知识（ECMA-262标准，变量类型，原型，作用域和异步等）  
Web-API(W3C标准，定义用于浏览器中js操作页面的API和全局变量)
- W3C标准中关于js的规定有：  
DOM操作  
BOM操作  
事件绑定  
ajax请求（包括http协议）

### 2. 浏览器

>浏览器内核（Rendering Engine）：渲染引擎，有时还包括js引擎。渲染引擎主要是负责HTML、CSS以及其他一些东西的渲染，而JS引擎则主要负责对javascript的渲染

- IE 6~11：Trident内核（又称IE内核）,对W3C标准支持差，从IE10开始支持ES6标准
- Chrome：基于Webkit内核浏览器，一经安装就时刻保持自升级，所以不用管它的版本，最新版早就支持ES6
- Safari：基于Webkit内核的浏览器，从OS X 10.7 Lion自带的6.1版本开始支持ES6
- Firefox：Gecko内核
- Opera：Presto内核（ 7.0及以上）

>不同的浏览器对JavaScript支持的差异主要是，有些API的接口不一样，比如AJAX，File接口。对于ES6标准，不同的浏览器对各个特性支持也不一样。

### 3. BOM（browser object model）
>BOM提供了独立于内容而与浏览器窗口进行交互的对象,主要用于管理窗口与窗口之间的通讯，因此其核心对象是window;由下列一系列相关的对象构成，并且每个对象都提供了很多方法与属性

- navigator对象:浏览器的信息  
appName：浏览器名称  
appVersion：浏览器版本  
language：浏览器设置的语言  
platform：操作系统类型  
userAgent：浏览器设定的用户代理头字符串

- history对象：保存了浏览器的历史记录  
back()方法：加载 history 列表中的前一个 URL  
forward()方法：加载 history 列表中的下一个 URL。
go()方法：相对当前所处的页面，加载 history 列表中的某个具体的页面。

- location对象：前页面的URL信息  
![location.png](http://upload-images.jianshu.io/upload_images/5150805-11016fbd73e9ebe3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 href：当前文档的完整URL  
protocol ：协议  
host：域名  
hostname ：主域名  
port：端口  
pathname：路径，URL中域名后的部分  
search：URL中的查询字符串  
hash：#符号后面的内容
- document对象：表示当前页面，整个DOM树的根节点
- screen对象：屏幕的信息  
height,width: 屏幕高和宽

### 3.DOM(document object model)
>W3C 文档对象模型 （DOM） 是中立于平台和语言的接口，它允许程序和脚本动态地访问和更新文档的内容、结构和样式。

- 数据结构：树
- 节点: nodeName,nodeType,nodeValue  
标签（元素）节点:元素名称，1，null  
属性节点:属性名称，2，属性值   
文本节点: #text,3,文本内容  
注释节点：#comment,8,注释内容
文档：#document，9，文档内容
- 节点关系：  
. childNodes：返回一个数组，由当前节点的所有的子节点构成  
. firstChild：返回第一个子节点  
. lastChild：返回最后一个子节点  
. parentNode：返回当前节点的父节点  
. previousSibling：返回给定节点的上一个同级节点  
. nextSibling：返回给定节点后一个同级节点  
. ownerDocument：给定节点的根节点   
. attributes：当前节点的所有属性节点
- 获取元素节点  
getElementById（）：根据ID值获取元素节点  
getElementsByClassName（）：根据class值获取元素节点（数组）    
getElementsByTagName（）：根据标签名获取节点   
getElementsByName（）：name属性值获取元素节点

- 获取属性 
获取行间样式表中的样式属性:element.style.attr  
获取外部样式表中的样式属性:element.currentStyle.attr(IE)或者window.getComputedStyle(element,null).attr(非IE，只读)
- 设置属性  
访问属性：.getAttribute（）还可以获取自定义属性的值  
直接修改：element.style.attr="newAttr"  
方法修改：. setAttribute(attr,value)  
删除属性:.removeAttribute(attr)

- 操作节点  
createElement():创建新的元素节点  
createTextNode():创建包含给定文本的新文本节点  
parentNode.appendChild(childNode):给指定节点的最后一个子节点列表之后添加一个子节点   
parentNode. insertBefore(newNode , currentNode)：在已有的子节点前插入一个新的子节点。  
parentNode.removeChild(node）：从子节点列表中删除某个节点  
parentNode.replaceChild（newnode,oldnode）:实现子节点（对象）的替换

- DOM节点的Attribute和property的区别
property是一个js对象的属性的修改  
Attribute是对html标签属性的修改

### 4. 相关题目
- DOM是哪种数据结构？树结构
- DOM操作的常用API有哪些？
获取dom节点，以及节点的property和attribute  
获取父节点，子节点  
增删节点，替换节点，
- DOM节点的attr和property有什么区别？  
前者是对html标签属性的修改，后者只是一个js对象的属性的修改