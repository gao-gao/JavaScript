### 1. 认识jQuery
#### 功能
1. 选取html元素并进行操作
2. CSS操作
3. html事件函数
4. javascript特效和动画
5. html DOM遍历和修改
6. ajax异步请求

#### 为什么使用
- 解决了js中的兼容问题，兼容于所有的主流浏览器

#### 安装
- 下载jQuery库（jquery.com）
- 从CDN中载入jQuery

#### 下载版本
- production version：用于实际的网站中（精简和压缩版）
- development version：用于测试和开发（未压缩，可读）

#### 使用
- 在`<script>`标签中引用文件

### 2. 语法
#### 基础语法： $(selector).action()
- 美元符号定义jQuery
- 选择符(selector)查询和查找html元素
- action()执行对元素的操作

#### 选择器：基于CSS选择器，扩展了自定义选择器
- 以$()开头
- #id
- .class
- 其他

#### 事件方法
- `$(document).ready()`：在文档完全加载完之后执行

- 大多数DOM事件都有一个等效的jQuery方法

### 3. 知识分类
- 选择器
- 事件方法
- 效果方法
- html、css方法
- 遍历方法
- ajax方法
- 相关属性
- 插件