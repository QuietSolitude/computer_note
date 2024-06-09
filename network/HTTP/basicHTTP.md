# HTTP Basics
## HTTP内容的结构

* HTTP：
  * HTTP请求(requests)：
    * 请求行：    
      * 请求方法：有GET、PUT、POST、DELETE、PATCH等等。用于指定请求的目的。详细内容见下方的介绍。
        * GET: 获取指定的资源。
        * PUT: 创建或者修改指定资源。
        * POST: 向服务器推送数据(创建或修改，或者产生要返回的临时文件)但最好别连续调用会带来额外的影响。
          * 比如创建用户，连续调用就会创建多个用户，而put方法不会只会创建一个用户。
        * DELETE: 删除指定资源。
        * PATCH: 更新局部资源。
      * 请求URL：指定请求的资源。  
        
    * 请求头：用于描述HTTP请求的附加信息。 例如：Host: developer.mozilla.org或者Accept-Language: fr
    * 请求体：请求的详细内容。
  * 注：一个请求中，请求行和请求头是必须存在的，请求体在不需要的情况下可以省略。没有请求体的请求叫做空请求。

  * HTTP响应(responses)：
    * 状态行(status line)：
      * 协议版本：通常是HTTP/1.1。
      * 状态码(status code)：表明请求是成功或失败，常见的状态码是200，404或者302。
      * 状态文本(status text)：简短的信息，描述HTTP的消息。eg HTTP/1.1 404 Not Found。
    * 消息报头(HTTP Headers)：用于描述HTTP响应的附加信息，例如关于服务器的信息。
    * 响应体(responses body)：响应的详细内容。
  * 注：一条响应中，状态行和状态码是必须存在的，响应体在不需要的情况下可以省略。比如具有状态码的响应可以没有响应体，404。

 
# HTTP服务：

* HTTP服务是通过HTTP协议与客户端进行交互，并且处理业务逻辑的服务器端程序。
* HTTP服务的基本流程是：
  * 1.接受请求。
  * 2.处理请求。
  * 3.发送响应。
* 注: HTTP服务在没有接到请求时不会进行任何处理，也不会发送响应给客户端。

# HTTP服务中的术语

* endpoint： 是由一个请求方法加上一个路径。 eg：GET/weather/qingdao
* 一个endpoint就代表HTTP服务里面的一个功能。

## 什么是endpoint方法
  * endpoint的请求方法是指组成endpoint的请求方法。 eg：app.get(URL,(req,res) => {});

## HTTP服务通过什么区分不同的功能
  * HTTP服务是通过请求行中的请求方法和URL来区别不同功能。
  


# word
* specify    