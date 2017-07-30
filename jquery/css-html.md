---
layout:     post
title:      "jquery-css,html"
date:       2017-05-02
categories: "jQuery"
author:     "gaogao"
tags:
 - jQuery   
description: "获取设置属性；获取设置文档、文本、表单value；通过类增删样式；通过css()进行样式操作；尺寸设置和获取"
---
### 1. 获取设置属性
attr()，提供回调函数。回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。
- .attr(属性名)：获取属性值  
`$("input:first").attr("value")`

- .attr(属性名，属性值)：设置属性值  
`$("input:eq(1)").attr("value","hello world!")`

- .attr(属性名，函数值)：设置属性函数值  
`$("input:eq(2)").attr("value",function(i,val){
	return '通过function设置'+val
	})`

- .attr(attributes)：设置多个属性值  
用键值对方式表示，“,” 隔开

- .removeAttr(属性名)：移除属性
	`$("input:eq(3)").removeAttr('value')`

> attribute：DOM节点自带的属性，例如id,class,title等  
property：DOM中的对象，其附加的内容，例如tagName,nodeName等，获取用prop()方法

- prop()：设置或返回被选元素的属性和值

- removeProp()：移除由 prop() 方法设置的属性

### 2. 获取设置文档、文本、表单value
#### .html()
设置或返回所选元素的内容（包括 HTML 标记）
- .html()

- .html(htmlString)

- .html(function(index,oldhtml()))

html()只能在HTML文档中使用，text()在XML和HTML中都可以使用

#### text()
设置或返回所选元素的文本内容
- .text()

- .text(textString)

- .text(function(index,text))

firefox 不支持innerText属性，用了类似的textContent属性，text()综合了两个属性，兼容所有浏览器

#### val() 
设置或返回表单字段的值
- .val()：无参数，获取集合中第一个元素的value值

- .val(value)：设置匹配集合中每个元素的值

- .val(function)：一个用来返回设置值的函数

> 1. 三者都拥有回调函数，回调函数有两个参数，一个是所选元素的索引，一个是原始值  
> 2. text()和html()不能用在表单元素上，val()只能用在表单元素上  
> 3. html()和val()用在多个元素时，只读取第一个元素，text()会读取所有选中元素的文本内容  
> 4. 三种方法同时运用在多个元素上替换选中元素的内容时，会替换掉所有选中元素的内容
> 5. 三种方法都可以使用回调函数的返回值动态地改变多个元素的内容

### 3. 通过类增删样式
#### 增加样式
- .addClass(className)：为每个元素匹配所要增加的一个或者多个样式类名

- .addClass(function(index,currentClass))：函数返回一个或者多个用空格隔开的要增加的样式名

#### 删除样式
- .removeClass(className)

- .removeClass(function(index,class))

#### 动态增删样式
- .toggleClass(className)：动态增删class 存在就删去 不存在就增加 会保留原有的class名，空格隔开

- .toggleClass(className,switch)：添加了一个布尔值，用于判断样式是否增删

- .toggleClass([switch])：一个用来判断样式类添加还是移除的布尔值

- .toggleClass(function(index,class,switch)[,switch])：返回在匹配的元素集合中的每个元素上用来切换的样式类名的一个函数，接收元素的索引位置和元素旧的样式类作为参数。

#### 检查类：hasClass() 
检查被选元素是否包含指定的类名称，包含则返回true

### 4. 通过css()进行样式操作
css() 方法设置或返回被选元素的一个或多个样式属性。
#### 获取
- .css(propertyName)：获取选取元素的样式值
$('p:eq(1)').text( $('.first').css("font-size") )

- .css(propertyNames)：传递一组数组，返回一个对象结果
```
<script>
var value = $('.first').css(["width","height"]);
		//因为获取的是一个对象，取到对应的值
		$('p:eq(2)').text( 'width:' + value.width +  ' height:' +value.height )
</script>
```

#### 设置
- .css(propertyName,value)：设置CSS  
`$('.fourth').css("background-color","red")`

- .css(propertyName,function)：传入一个回调函数，返回取到对应的值进行处理  
```
$('.sixth').css("width",function(index,value){
		    value = value.split("px");
		    分割字符串取前者数字
		    return (Number(value[0])+50)+value[1]
		})
```

- .css(properties)：传入一个对象，同时设置多个样式，多个属性用,分开
			`
            $('.seventh').css({
		    "font-size":"15px",
		    "background-color":"red",
		    "border":"1px solid red"
			})
            `
>1. 支持驼峰写法和大小写混搭的写法，因为内部做了容错处理  
>2. 当一个数只作为值value时，jQuery会将其转化为字符串并加上单位
>3. 颜色RGB，尺寸px，采用了统一的处理

#### 和通过类增删样式的区别
- class是外部样式，可维护性较强；.css是内部样式，灵活性较强

- 一般静态结构都确定了布局规则，用前者；动态结构经常变化，多用后者

### 5. 尺寸设置和获取
#### width() 和 height()
设置或返回元素的宽高（不包括内边距、边框或外边距）

#### innerWidth() 和 innerHeight()
返回元素的宽高（包括内边距）

#### outerWidth() 和 outerHeight() 
返回元素的宽高（包括内边距和边框）

#### scrollLeft()和scrollTop()
设置或返回被选元素的水平/垂直滚动条位置

#### offset()
设置或返回被选元素相对于文档的偏移坐标
- 参数：`{top:value,left:value}`

####  position() 
- 返回第一个匹配元素的位置（相对于它的父元素）,该方法返回一个带有两个属性（以像素为单位的 top 和 left 位置）的对象。









