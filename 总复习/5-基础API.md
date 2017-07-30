### 1. 日期
- Date():返回当前日期和时间
- getDate():查看date对象并返回日期 1-31
- getDay():返回星期几 0-6
- getHours():返回小时数 0-23
- getMinutes():返回分钟数 0-59
- getMonth():返回月份值 0-11
- getSeconds():返回秒数
- getTime():返回毫秒数
- getYear():返回年份
- getFullYear():完整值

### 2. 数组
- forEach：遍历所有元素
```
var arr=[1,2,3]
arr.forEach(function(item,index){console.log(index,item)})
//结果：
0 1
1 2
2 3
```
- every：判断所有元素是否都符合条件
```
var arr=[1,2,3];
var result=arr.every(function(item,index){
//判断数组中的所有元素都满足"<4"这个条件
if(item<4){return true}
})
console.log(result);
//打印true
```
- some：判断是否有至少一个元素符合条件
```
var arr=[1,2,3];
var result=arr.some(function(item,index){
//判断数组中至少有一个元素满足">2"这个条件
if(item>2){return true;}
})
console.log(result);
//true
```
- sort：排序
```
var arr=[1,5,4,2];
var result=arr.sort(function(a,b){
//从小到大排列,从大到小排列return b-a即可
return a-b})
console.log(result);
//[1,2,4,5]
```
- map：对元素重新组装，生成新数组
```
var arr=[1,2,3,4,5]
var result=arr.map(function(item,index){
将元素重新组装并返回
return item*item
})
console.log(result);
//[1, 4, 9, 16, 25]
```
- filter：过滤符合条件的元素
```
var arr=[1,2,3,4,5];
var result=arr.filter(function(item,index){
//通过某一个条件过滤掉数组中不符合条件的元素，剩下的元素形成新数组
if(item>2){return true}
})
console.log(result);
//[3,4,5]
```
- indexOf：搜索一个指定的元素的位置
- slice：截取Array的部分元素，然后返回一个新的Array
```
var arr=[1,2,3,4,5,6,7];
//将索引值为2到5的元素截取形成新数组，包括2，不包括5
var result=arr.slice(2,5);
console.log(result);
//[3,4,5]
```
- push：向Array的末尾添加若干元素
- pop：把Array的最后一个元素删除掉
- unshift：往Array的头部添加若干元素
- shift：把Array的第一个元素删掉
- reverse：把整个Array中所有元素反转顺序
- splice：从指定的索引开始删除若干元素，然后再从该位置添加若干元素
```
var arr=[1,2,3,4,5];
//从索引2开始，删去后面三个元素“3，4，5”，然后添加三个元素“a,b,c”
var result=arr.splice(2,3,"a","b","c");
//返回删去的元素数组
console.log(result);
//[3,4,5]
//返回经过删增之后的数组
console.log(arr);
[1,2,"a","b","c"]
```
- concat：将当前数组和传入的数组连接起来并返回一个新的数组，原本数组不改变
```
var arr = ['A', 'B', 'C'];
var result = arr.concat([1, 2, 3]);
result; // ['A', 'B', 'C', 1, 2, 3]
arr; // ['A', 'B', 'C']
```
- join：将数组的每个元素都用指定的字符串连接起来
```
var arr = ['A', 'B', 'C', 1, 2, 3];
arr.join('-'); // 'A-B-C-1-2-3'
```

### 3. 对象
- hasOwnProperty()：判断一个属性是自身拥有的，而不是通过继承得到（原型链）

### 4. 字符串
- toUpperCase：转换为大写
- toLowerCase：转换为小写
- indexOf：搜索指定字符串出现的位置
- substring：返回指定索引区间的子串

### 5. 相关题目
- 获取2017-06-10格式的日期

```
function formatDate(date){
if(!date){date=new Date()}
    var year=date.getFullYear();
    var month=date.getMonth()+1;
    var day=date.getDate()
if(month<10){month="0"+month;}

if(day<10){month="0"+day;}
return year+"-"+month+"-"+day
}
var date=new Date()
var result=formatDate(date);
console.log(result);
```

- 获取随机数，要求长度一致的字符串格式

```
var number=Math.radom()
var number=number+"00000";
var number=number.slice(0,5);
console.log(number);
//0.123
```

- 写一个能遍历对象和数组的通用forEach函数

```
function forEach(obj,fn){
	var key;
	if(obj instanceof Array){
		obj.forEach(function(item,index){
			fn(index,item)
		})
	}else{
		for(key in obj){
			fn(key,obj[key])
		}
	}
}
var arr=[1,2,3]
forEach(arr,function(index,item){
	console.log(index,item)
})
var obj={x:100,y:200}
forEach(obj,function(key,value){
	console.log(key,value)
})
```