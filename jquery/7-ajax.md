
### 1. load()
从服务器加载数据，并把返回的数据放入被选元素中
`$(selector).load(URL,data,callback)`
- URL：希望加载的URL，必需参数
- data：规定与请求一同发送的查询字符串键/值对集合，可选参数
- callback ： load() 方法完成后所执行的函数名称

### 2. get() 和 post() 
#### get():通过 HTTP GET 请求从服务器上请求数据
`$.get(URL,callback)`

#### post(): HTTP POST 请求从服务器上请求数据
`$.post(URL,callback)`