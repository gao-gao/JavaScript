---
layout:     post
title:      "jquery-dom"
date:       2017-05-04
categories: "jQuery"
author:     "gaogao"
tags:
 - jQuery   
description: "动态创建节点和节点属性；插入元素；删除元素；和事件相关的元素处理；替换和嵌套；查询第一个定位的祖先元素；转义选择器中的特殊字符；cssHooks"
---
### 1. 动态创建节点及节点属性：
语法：$("html结构")
#### 创建元素节点：
`$("<div></div>")`
#### 创建文本节点：
`$("<div>我是文本节点</div>")`
#### 创建属性节点：
`$("<div id='test' class='aaron'>我是文本节点</div>")`

### 2. 插入元素
#### 动态创建的元素是临时存放在内存中，需要将其放到页面文档中呈现出来
- B.append(A)：和原生的appendChild方法类似，将A加到B的结尾
- B.appendTo(A)：和上法相反，将B加到A的结尾里

- B.prepend(A)：将A加到B的开头
- B.prependTo(A)：将B加到A的开头

- after()：在被选中元素之后插入内容
- before()：在被选元素之前插入内容

- insertAfter()：在被选元素后插入 HTML 元素
- insertBefore()：在被选元素前插入 HTML 元素


### 3. 删除元素
- remove()： 删除被选元素及其子元素，接受一个参数，对被删元素进行过滤

- empty()：删除被选元素的子元素

### 4. 和事件相关
#### clone() 
生成被选中元素的副本，包含子节点、文本和属性。
- $(selector).clone(true|false)，true规定需复制事件处理程序;false不复制

#### detach()
移除被选元素，包括所有的文本和子节点，但会保留数据和事件
- 会保留移除元素的副本，允许它们在以后被重新插入

### 5. 替换与嵌套
#### 替换
- replaceAll()：把被选元素替换为新的 HTML 元素  
`$(content).replaceAll(selector)`

- replaceWith()：把被选元素替换为新的内容  
`$(selector).replaceWith(content,function(index))`

####嵌套
- unwrap()：移除被选元素的父元素

- wrap()：在每个被选元素的周围用 HTML 元素包裹起来

- wrapAll()：在所有被选元素的周围用 HTML 元素包裹起来

- wrapInner()：在每个被选元素的内容周围用 HTML 元素包裹起来

### 6. 查询
- offsetParent()：返回第一个定位的祖先元素

### 7. $.escapeSelector() 
转义CSS选择器中有特殊意义的字符或字符串
- 在jQuery 3.0中被添加，可在所有jQuery支持的浏览器中使用

- 转义：. 或者 ：或者 #

### 8. $.cssHooks
提供了一种方法通过定义函数来获取和设置特定的CSS值
- 目的：标准化 CSS 属性名或创建自定义属性

