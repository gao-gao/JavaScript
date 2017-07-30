### 1. 基本选择器
- id选择器：$("#id")

- 类选择器：$(".class")

- 元素选择器：$("element")

- 全选择器：$("*")

### 2. 层次选择器
- 子元素：$("parent>child")

- 后代元素：$("ancestor descendant")

- 相邻兄弟：$("prev+next")

- 一般兄弟：$("prev~siblings")

### 3. 基本筛选选择器
- $(":first") 第一个

- $(":last") 最后一个元素

- $(":not(selector)") 去除不匹配的  

- $(":eq(index)") 选中索引值所在元素

- $(":gt(index)") 大于索引值

- $(":lt(index)") 小于索引值

- $(":even") 偶数索引值

- $(":odd") 奇数索引值

- $(":header") 标题元素

- $(":lang(language)") 指定语言

- $(":root") 文档根元素

- $(":animated") 正在执行动画效果的元素 

### 4. 内容选择器
- $(":contains(text)") 包含指定文本  
$("div:contains('hello world')")

- $(":has(selector)") 包含指定元素  
$("div:has(a)")

- $(":parent") 含有子元素或者文本的  
$("div:parent")

- $(":empty") 所有没有子元素的,连文本都没有，但可以添加文本  
$("div:empty")

### 5. 可见性筛选选择器
- $(":visible") 选择所有显示的元素

- $(":hidden") 选择所有隐藏的元素

### 6. 属性选择器
- ("[att]") 选择具有指定属性的元素，其值可以为任意值  
$("div[id]")

- ("[att='value']") 属性值为指定字符串  
$("div[id='target']")

- ("[att!='value']") 属性值不含指定字符串或不含指定属性  
$("div[checked!]")

- ("[att|='value']") 属性值以指定字符串为前缀--该字符串后跟一个"-"  
$("div[name|'-']")

- ("[att^='value']") 属性值以指定字符串开头  
$("div[href^='www']")

- ("[att$='value']") 属性值以指定字符串结尾，区分大小写  
$("div[href$='163.com']")

- ("[att*='value']") 属性值包含指定字符串  
$("div[href*='baidu']")

- ("[att~='value']") 属性值用空格分隔的某个值包含指定字符串  
$(.head[class~='h1'])

- ("[att1][att2]") 选择匹配所有的指定属性筛选器  
$("a[class~='main'][href^='www']")
### 7. 子元素选择器
- (":first-child")  
$(".first-div a:first-child")

- (":last-child")  
$(".first-div a:last-child")

- (":only-child") 父元素的唯一子元素  
$(".first-div a:only-child")

- (":nth-child()") 索引值从1开始  
$(".first-div a:nth-child(2)")

- (":nth-last-child()") 倒数 索引值从1开始  
$(".first-div a:nth-last-child(2)")
### 8. 表单选择器
- $(":input") 

- $(":text") 文本框

- $(":password") 密码框

- $(":radio") 单选按钮

- $(":checkbox") 复选框

- $(":submit") 提交按钮

- $(":image") 图像域 

- $(":reset") 重置按钮

- $(":button") 所有按钮

- $(":file") 文件域

> 大部分表单选择器可以使用属性筛选器替换：$("[type=password]")

### 9. 表单对象属性筛选选择器
- $(":enabled") 可用的表单元素

- $(":disabled") 不可用的表单元素

- $(":checked") 选中的input元素  
$("input:checked") 不加input限定可能会误选option元素

- $(":selected") 选中的option元素 下拉框

### 10. 特殊选择器
- $(this) 将this加工成jQuery对象，可以调用jQuery的方法和属性值
	