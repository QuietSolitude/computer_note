# Express Basics

## 什么是Express
* Express是一个辅助构建HTTP服务的框架，实现了一些写HTTP服务必要的功能。比如给endpoint注册handler或者给lambda提供参数等。
* 注：一个endpoint可以注册多个handler。 eg：app.get(URL, () => {}, () => {})。

## Express的安装
  * $ npm i express或者npm install express。

## Express文件的基础结构

```js

    app.get(URL, (req, res) => { ... });
    // 用于定义一个endpoint的请求方法、URL以及Handler。
    // 其中：
    //   方法名get为该endpoint的请求方法，可以将get替换为其他HTTP的请求方法，如post、put、delete等。
    //   URL为该endpoint的URL路径，例如/path/to/resource。其中可以添加路径参数，例如/path/to/:name中的name即为路径参数，可以被任何不含有斜杠的字符串替代。
    //   第二个参数的lambda为该endpoint的handler，当服务器接到了含有相应方法以及路径的HTTP请求后，就会调用这个handler进行请求的处理。

```

## Express的json解析器
* Express实现的一个json解析器，默认情况下不会起任何作用

* 
  * 调用express.json()会返回一个Lambda的值（也就是json解析器）启动json解析器，这个函数要在自己写的lambda前面. eg：app.post(URL, express.json(), () => {});
  * JSON规定字符串要满足JSON格式的要求，必须要有双引号。例如 字符串的 "{ \"id\": 123 }"打印 "id" : 123。
    * JavaScript里面的的object是左边是键，键可以加引号也可以不加，右边是值。eg：{ id : 123}或者是{ "id": 123}。
      
  * 注： 在JS里面，匿名函数，Lambda，和函数是一个单独的类型,所以可以使用这些当函数的参数。当函数需要一段逻辑，这段逻辑必须在函数规定的特定的时间点运行，而不是在调用函数的瞬间运行时，就需要传入一个函数当参数。

## Express运行原理


