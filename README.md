# NodeJS-Learning
## HTTP请求的过程 ##
（1）浏览器先搜索自身的DNS缓存

（2）操作系统搜索自身的DNS缓存（浏览器没有找到缓存或者缓存已经失效）

（3）读取本地的HOST文件

（4）浏览器发起一个DNS的一个系统调用

         宽带运营商服务器查看本身缓存

         运营商服务器发起一个迭代DNS解析的请求

         运营商服务器把结果返回操作系统内核同时缓存起来

         操作系统内核把结果返回浏览器

         浏览器就拿到了www.imooc.com的IP地址
（5）浏览器获得域名对应的IP地址后，发起HTTP“三次握手”

（6）TCP/IP链接建立起来后，浏览器就可以向服务器发送HTTP请求了

（7）服务器端接受到了这个请求，根据路径参数，经过后端的一些处理之后，把处理后的结果数据返回给浏览器，比如页面完整的html代码等返回给浏览器

（8）浏览器拿到了完整的html代码后，在解析和渲染这个页面的时候，里面的JS,CSS,图片静态资源，他们同样也是一个个http请求，都要经过上面的主要七个步骤。

（9）浏览器根据拿到的资源对页面进行渲染，最终把一个完整的页面呈现给了用户。
## 状态码 ##
- 1xx：接受
  - 200：ok；
- 2xx：成功
- 3xx：重定向
- 4xx：客户端语法错误
  - 401：请求没有经过授权；
  - 403：服务器收到请求，拒绝提供服务；
  - 404：没找到；
- 5xx：服务器端错误
  - 500：服务器发生未知错误；
  - 503：服务器不处理，过段时间；
 ## 实现异步的方式 ##
   - callback 回调方式

   - 事件机制（监听+触发）【订阅者|观察者】模式

   - promise：表示一个异步操作的最终结果，以同步的方式来写代码，执行的操作是异步的，但是保证程序的执行顺序是同步的。
 ## Promise对象的三种状态 ##
  - 未完成(pending)

  - 已完成(fulfilled)

  - 失败(rejected)
 ## Promise A 与 A+ 不同点 ##
  - A+ 规范通过术语 thenable 来区分promise对象
  - A+ 定义 onFulfilled/onRejected 必须是作为函数来调用，而且调用过程必须是异步的
  - A+ 严格定义了 then 方法链式调用是 onFulfilled/onRejected 的调用顺序
  
 ## Promise then 方法 ##
  promiseObj.then(onFulfilled, onRejected)
 
  onFulfilled = function(value){
     return promiseObj2
  }
 
  onRejected = function(err){}
