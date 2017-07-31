### 1. 隐藏和显示（display属性）
#### hide()：`$(selector).hide(speed,)`
隐藏已显示的元素
- speed：规定速度，毫秒或“slow”,“fast”
- callback：规定隐藏完成之后执行的函数

#### show()：`$(selector).show(speed,callback)`
显示被隐藏的元素

#### toggle()：`$(selector).toggle(speed,callback)`
显示被隐藏的元素，并隐藏已显示的元素

### 2. 淡入淡出（透明度）
#### fadeIn()：`$(selector).fadeIn(speed,callback)`
淡入已隐藏的元素

#### fadeOut()：`$(selector).fadeOut(speed,callback)`
淡出可见元素

#### fadeToggle()：`$(selector).fadeToggle(speed,callback)`
元素已淡入时会淡出，已淡出时会淡入

#### fadeTo()：`$(selector).fadeTo(speed,opacity,callback)`
opacity参数设置透明度（0-1之间）

### 3. 滑动（高度）
#### slideDown()：`$(selector).slideDown(speed,callback)`
向下滑动元素

#### slideUp()：`$(selector).slideUp(speed,callback)`
向上滑动元素

#### slideToggle()：`$(selector).slideToggle(speed,callback)`
在前面两种之间自动切换

### 4. 自定义动画 animate()
#### 语法：`$(selector).animate({params},speed,callback)`
- params参数：定义形成动画的CSS属性  
键值对用{}包起来，键值对之间用,分离  
属性和属性值间用：链接，属性名采用驼峰命名法  
属性值用""包围

- 使用相对值：在值的前面加 += 或 -=

- 使用预定义的值：show,hide,toggle

- 使用队列功能，创建多个动画形成队列依次执行

### 5. 停止动画stop() 
适用于所有jQuery效果函数
- `$(selector).stop(stopAll,goToEnd);`默认值都是false

- stop()：停止当前动画，后续动画继续

- stop(true)：停止所有队列的动画

- stop(true,true)：当前动画停止，直接跳到当前动画的最终状态

### 6. 链(Chaining)
在相同的元素上运行多条 jQuery 命令，一条接着另一条，这样浏览器就不用多次查找目标元素了

### 7. 队列
#### queue()
- 显示被选元素的排队函数
- queue(func)：把函数加入队列

#### dequeue() 
移除下一个排队函数，然后执行函数

#### clearQueue() 
从尚未运行的队列中移除所有项目

#### delay()
对被选元素的所有排队函数（仍未运行）设置延迟

#### finish()
对被选元素停止、移除并完成所有排队动画
	