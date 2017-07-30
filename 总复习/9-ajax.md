### 1. ajax是什么？
#### 全称：
 - Asynchronous JavaScript and XML（异步的 JavaScript和XML）
 
#### 特点：
- 不重新加载整个页面的情况下，可以与服务器交换数据并更新部分网页内容

>传统的网页不用ajax技术的网页，想要更新内容或者提交一个表单，需要重新载整个入页面；使用ajax技术的网页，通过在后台跟服务器进行少量的数据交换，网页就可以实现异部局部更新。

#### 工作原理：
- 客户端触发事件向服务器发送请求，服务器响应请求返回数据给客户端，客户端根据返回结果进行局部更新。

#### 结合知识点
- XMLhttpRequest对象（异步的和服务器交换数据）

- JavaScript/DOM (信息显示/交互)

- CSS (给数据定义样式)

- XML (作为转换数据的格式)

### 2. ajax中的同步和异步
#### 同步：
完成表单时，点击提交，发现未填写完整，得重新填写，不断提交不断修改客户端发出请求--服务器端处理（此时客户端在等待）--服务器端响应（此时客户端重新载入）此过程不断重复，直至用户完成整张表单

#### 异步：
填写表单上的项目时，客户端就像服务器发出请求并且响应，实时将填写错误在页面上显示出来，此过程中不会重新加载整个页面

### 3 http相关
#### 完整的http请求过程：
1. 建立TCP连接
2. web浏览器向web服务器发送请求命令
3. web浏览器发送请求头信息
4. web服务器应答
5. web服务器发送应答头信息
6. web服务器向浏览器发送数据
7. web服务器关闭TCP连接

#### http请求
1. http请求的方法或动作，例如get/post
2. 正在请求的url，请求的地址
3. 请求头，包含一些客户端环境信息，身份验证信息等
4. 请求体，也就是请求正文，包含客户提交的查询字符串信息、表单信息

#### http响应：
1. 一个数字和文字组成的状态码，用来显示请求是成功还是失败
2. 响应头，和请求头一样包含很多有用的信息，例如服务器类型、日期时间、内容类型和长度等
3. 响应体，即响应正文 

#### status状态码：由三位数字构成，首位数字定义了状态码的类型
- 1XX:信息类，表示收到web请求，正在进一步处理中
- 2XX:成功，表示用户请求被正确接收、理解和处理
- 3XX:重定向，表示请求没有成功，客户必须采取进一步的动作
- 4XX:客户端错误，表示客户端提交的请求有错误
- 5XX:服务器错误，表示服务器不能完成对请求的处理

### 4. 创建对象
#### XMLHttpRequest对象：
用于在后台与服务器交换数据

#### 创建XHR
- IE7+、Firefox、Chrome、Safari 以及 Opera  
var xhr=new XMLHttpRequest();

- IE5 和 IE6  
var xhr=new ActiveXObject("Microsoft.XMLHTTP");

#### 兼容处理
```
<script>
    var xml;
    if(window.XMLHttpRequest){
        //  IE7+, Firefox, Chrome, Opera, Safari内置有XHR对象
        xml = new XMLHttpRequest();
    }else{
        //IE6, IE5
        xml = new ActiveXObject("Microsoft.XMLHTTP")
    }
</script>
```

### 5. 向服务器发送请求
#### open() 和 send() 方法：
- open(method,url,async) 初始化请求
method：请求的类型（get/post）  
url：文件在服务器的位置（可以是任何类型的文件）
async：是否异步，true(异步)；false(同步)

- send(string)  
参数存在的时候仅用于post请求

#### get和post
- get
1. 一般用于信息获取
2. 使用URL传递参数（所有的变量名和值都在URL上，对任何人可见）
3. 对所发送信息的数量有限制，一般在2000个字符
4. 幂等：查询多次不改变信息，不推荐使用其改变信息

- post
1. 一般用于修改服务器上的资源
2. 对所发送信息的数量无限制
3. 发送的所有信息会嵌入请求体中

#### 异步
在等待服务器响应时执行其他脚本，当响应就绪后对响应进行处理

#### 同步
等到服务器响应就绪才继续执行。如果服务器繁忙或缓慢，应用程序会挂起或停止。

### 6. 服务器响应
##### 通过XHR属性和方法获取来自服务器的响应

- responseText ：获得字符串形式的响应数据

- responseXML：获得XML形式的响应数据

- status和statusText:以数字和文本形式返回http状态码

- getAllResponseHeader():获取所有的响应报头

- getResponseHeader():查询响应中的某个字段的值

#### readyState：存有XMLHttpRequest的状态信息。
- 0：请求未初始化，open还没有调用

- 1：服务器连接已建立，open已经调用了

- 2：请求已接收，接收到头信息了

- 3：请求处理中，接收到响应主体了

- 4：请求已完成，且响应已就绪（完成）

#### 常用status：
- 200: "OK"

- 404: 未找到页面

##### onreadystatechange事件
- 每当 readyState 改变时，就会触发 onreadystatechange 事件
```
<script>
    var request = new XMLHttpRequest();
    request.open("get","get.php",true);
    request.send();
    request.onreadystatechange=function(){
        if(request.readyState===4&&request.status===200){
            //请求你完成且响应就绪后执行函数
            request.responseText
        }
    }
</script>
```

#### 使用回调函数
如果存在多个ajax任务，可以为创建 XMLHttpRequest 对象编写一个标准的函数，并为每个 AJAX 任务调用该函数。该函数调用应该包含 URL 以及发生 onreadystatechange 事件时执行的任务（每次调用可能不尽相同）

### 7. 跨域
#### 浏览器的同源策略
- 同源：URL由协议、域名、端口和路径组成，如果两个URL的协议、域名和端口相同，则表示他们同源。

- 浏览器的同源策略，限制了来自不同源的"document"或脚本，对当前"document"读取或设置某些属性，是浏览器上为安全性考虑实施的非常重要的安全策略。

#### 可跨域的标签
`<script>、<img>、<iframe>、<link>`

#### 跨域注意事项
1. 所有的跨域请求都必须经过信息提供方的允许
2. 如果未经允许即可获取，那是浏览器同源策略出现漏洞

#### 跨域的几种实现方式
1. JSONP（`<script>`）
2. 服务器端设置http header(加入扩展字段)
3. 使用代理
