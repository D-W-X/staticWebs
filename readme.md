# HTTP request

HTTP\:超文本传输协议（HyperText Transfer
Protocol，缩写\:HTTP）是一种用于分布式、协作式和超媒体信息系统的应用层协议。
内容\:

- 请求行(Request-Line)\: 请求方式(method
  token)+资源位置(Request-URI)+协议版本(protocol version)+结束标志(CRLF
  or Carriage-Return Line-Feed)回车换行

  - 请求方式\:
    - GET\:Should only retrieve data and should have no other effect on
      the data.
    - HEAD\:Transfers the status line and the header section only.
    - POST\:Send data to the server.
    - PUT\:Replaces target resource with the uploaded content.
    - DELETE\:Removes target resource.
    - CONNECT\:Establishes a tunnel to the server identified.
    - OPTIONS\:Describe the communication options for the target
      resource.
    - TRACE\:Performs a message loop back test along with the path to
      the target resource.

  - 资源位置\:
    - \*\:请求不特殊指定一个资源，如\:`OPTIONS * HTTP/1.1`
    - 绝对地址(absoluteURI)\:当前请求作为代理，返回被代理页面的response
    - 相对地址\:最常见的请求方式，一般是相对于主机`host`参数的资源位置。
    - 必须有一个位置，如果原请求没有，它一定是`/`。

- 请求头\:
  请求头允许客户端向服务器传输一些额外的关于本次请求和客户端自身的修饰性信息。

  - 标准请求头
    >| 协议头字段          | 说明                                                                                                                                                                                      | `示例`                                                                              | 是否常用     |
    >|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------|:-------------|
    >| Accept              | 能够接受的回应内容类型（Content-Types）                                                                                                                                                    | `Accept: text/plain`                                                                | 常设         |
    >| Accept-Charset      | 能够接受的字符集                                                                                                                                                                           | `Accept-Charset: utf-8`                                                             | 常设         |
    >| Accept-Datetime     | 能够接受的按照时间来表示的版本                                                                                                                                                             | `Accept-Datetime: Thu, 31 May 2007 20\:35\:00 GMT`                                  | 临时         |
    >| Accept-Encoding     | 能够接受的编码方式列表。参考HTTP压缩                                                                                                                                                       | `Accept-Encoding: gzip, deflate`                                                    | 常设         |
    >| Accept-Language     | 能够接受的回应内容的自然语言列表                                                                                                                                                           | `Accept-Language: en-US`                                                            | 常设         |
    >| Authorization       | 用于超文本传输协议的认证的认证信息                                                                                                                                                         | `Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`                                 | 常设         |
    >| Cache-Control       | 用来指定在这次的请求/响应链中的所有缓存机制都必须遵守的指令                                                                                                                                 | `Cache-Control: no-cache`                                                           | 常设         |
    >| Connection          | 该浏览器想要优先使用的连接类型                                                                                                                                                             | `Connection: keep-alive`,`Connection\: Upgrade`                                     | 常设         |
    >| Content-Length      | 以八位字节数组（8位的字节）表示的请求体的长度                                                                                                                                               | `Content-Length: 348`                                                               | 常设         |
    >| Cookie              | 之前由服务器通过Set-Cookie发送的一个 超文本传输协议Cookie                                                                                                                                   | `Cookie: $Version=1; Skin=new;`                                                     | 常设\: 标准  |
    >| Date                | 发送该消息的日期和时间(按照 RFC 7231 中定义的"超文本传输协议日期"格式来发送)                                                                                                                | `Date: Tue, 15 Nov 1994 08:12:31 GMT`                                               | 常设         |
    >| Expect              | 表明客户端要求服务器做出特定的行为,没有已知的浏览器会使用这个消息头。                                                                                                                        | `Expect: 100-continue`                                                              | 常设         |
    >| From                | 发起此请求的用户的邮件地址                                                                                                                                                                 | `From: user@example.com`                                                            | 常设         |
    >| Host                | 服务器的域名(用于虚拟主机 )，以及服务器所监听的传输控制协议端口号。如果所请求的端口是对应的服务的标准端口，则端口号可被省略。自超文件传输协议版本1.1（HTTP/1.1）开始便是必需字段                | `Host: en.wikipedia.org:80`,`Host: en.wikipedia.org`                                | 常设         |
    >| If-Match            | 仅当客户端提供的实体与服务器上对应的实体相匹配时，才进行对应的操作。主要作用时，用作像 PUT 这样的方法中，仅当从用户上次更新某个资源以来，该资源未被修改的情况下，才更新该资源                   | `If-Match: "737060cd8c284d8af7ad3082f209582d"`                                      | 常设         |
    >| If-Modified-Since   | 允许在对应的内容未被修改的情况下返回304未修改（ 304 Not Modified ）                                                                                                                         | `If-Modified-Since: Sat, 29 Oct 1994 19\:43\:31 GMT`                                | 常设         |
    >| If-None-Match       | 允许在对应的内容未被修改的情况下返回304未修改（ 304 Not Modified ），参考 超文本传输协议 的实体标记                                                                                          | `If-None-Match: "737060cd8c284d8af7ad3082f209582d"`                                 | 常设         |
    >| If-Range            | 如果该实体未被修改过，则向我发送我所缺少的那一个或多个部分；否则，发送整个新的实体                                                                                                           | `If-Range: "737060cd8c284d8af7ad3082f209582d"`                                      | 常设         |
    >| If-Unmodified-Since | 仅当该实体自某个特定时间已来未被修改的情况下，才发送回应                                                                                                                                    | `If-Unmodified-Since: Sat, 29 Oct 1994 19\:43\:31 GMT`                              | 常设         |
    >| Keep-Alive          | 允许消息发送者暗示连接的状态，还可以用来设置超时时长和最大请求数                                                                                                                            | Keep-Alive: timeout=5, max=1000                                                     | 常设         |
    >| Max-Forwards        | 限制该消息可被代理及网关转发的次数                                                                                                                                                         | `Max-Forwards: 10`                                                                  | 常设         |
    >| Origin              | 发起一个针对 跨来源资源共享 的请求（要求服务器在回应中加入一个‘访问控制-允许来源’（'Access-Control-Allow-Origin'）字段）                                                                   | `Origin: http://www.example-social-network.com`                                     | 常设\: 标准  |
    >| Pragma              | 与具体的实现相关，这些字段可能在请求/回应链中的任何时候产生多种效果。                                                                                                                        | `Pragma: no-cache`                                                                  | 常设但不常用 |
    >| Proxy-Authorization | 用来向代理进行认证的认证信息                                                                                                                                                               | `Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`                           | 常设         |
    >| Range               | 仅请求某个实体的一部分。字节偏移以0开始。参见字节服务                                                                                                                                       | `Range: bytes=500-999`                                                              | 常设         |
    >| Referer \[sic\]     | 表示浏览器所访问的前一个页面，正是那个页面上的某个链接将浏览器带到了当前所请求的这个页面                                                                                                     | `Referer: http://en.wikipedia.org/wiki/Main_Page`                                   | 常设         |
    >| TE                  | 浏览器预期接受的传输编码方式\:可使用回应协议头 Transfer-Encoding 字段中的值；另外还可用"trailers"（与"分块 "传输方式相关）这个值来表明浏览器希望在最后一个尺寸为0的块之后还接收到一些额外的字段 | `TE: trailers, deflate`                                                             | 常设         |
    >| Upgrade             | 要求服务器升级到另一个协议                                                                                                                                                                 | `Upgrade: HTTP/2.0, SHTTP/1.3, IRC/6.9, RTA/x11`                                    | 常设         |
    >| User-Agent          | 浏览器的浏览器身份标识字符串                                                                                                                                                               | `User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv\:12.0) Gecko/20100101 Firefox/21.0` | 常设         |
    >| Via                 | 向服务器告知，这个请求是由哪些代理发出的。                                                                                                                                                  | `Via: 1.0 fred, 1.1 example.com (Apache/1.1)`                                       | 常设         |
    >| Warning             | 一个一般性的警告，告知，在实体内容体中可能存在错误                                                                                                                                          | `Warning: 199 Miscellaneous warning`                                                | 常设         |

    1. Accept:\<MIME_type\>/\<MIME_subtype\>\[;q=\]
    2. Accept-Charset:\<charset\>\[;q=\]
    3. Accept-Encoding:Multiple_algorithms\[;q=\]
    4. Authorization:\<type\>\<credentials\>
    5. Cache-Control
       - 可缓存性
         1. public:表明响应可以被任何对象（发送请求的客户端，代理服务器，等等）缓存。
         2. private:表明响应只能被单个用户缓存，不能作为共享缓存（即代理服务器不能缓存它）,可以缓存响应内容。
         3. no-cache:在释放缓存副本之前，强制高速缓存将请求提交给原始服务器进行验证。
         4. only-if-cached:表明客户端只接受已缓存的响应，并且不要向原始服务器检查是否有更新的拷贝
       - 到期
         1. max-age=\<seconds\>:设置缓存存储的最大周期，超过这个时间缓存被认为过期(单位秒)。与Expires相反，时间是相对于请求的时间。
         2. s-maxage=\<seconds\>:覆盖max-age 或者 Expires
            头，但是仅适用于共享缓存(比如各个代理)，并且私有缓存中它被忽略。
         3. max-stale\[=\<seconds\>\]:表明客户端愿意接收一个已经过期的资源。可选的设置一个时间(单位秒)，表示响应不能超过的过时时间。
         4. min-fresh=\<seconds\>:表示客户端希望在指定的时间内获取最新的响应。
       - 重新验证和重新加载
         1. must-revalidate:缓存必须在使用之前验证旧资源的状态，并且不可使用过期资源。
         2. proxy-revalidate:与must-revalidate作用相同，但它仅适用于共享缓存（例如代理），并被私有缓存忽略。
       - 其他
         1. no-store:缓存不应存储有关客户端请求或服务器响应的任何内容。
         2. no-transform:不得对资源进行转换或转变。Content-Encoding,
            Content-Range,
            Content-Type等HTTP头不能由代理修改。例如，非透明代理可以对图像格式进行转换，以便节省缓存空间或者减少缓慢链路上的流量。
            no-transform指令不允许这样做。
    6. Cookie:name=value; name2=value2; name3=value3.
    7. Date: \<day-name\>, \<day\> \<month\> \<year\>
       \<hour\>\:\<minute\>\:\<second\> GMT
    8. Host:\<host\>:\<port=80\>
    9. Keep-Alive:timeout=\*, max=\*

  - 内容协商(Content Negotiation)\:
    使同一个统一资源标志符（URI）上的文档可以根据用户代理中指定的适用信息提供不同的版本。
    - 服务器驱动模式\:
      <br>用户代理在HTTP头Accept中列出和提供可接受的媒体类型及相应的质量评级。服务器按照用户代理所提供的这些参数选择提供最适合用户代理的资源版本。<br>
      如\:`Accept-Language\: de; q=1.0, en; q=0.5 \n Accept\: text/html;
      q=1.0, text/*; q=0.8, image/gif; q=0.6, image/jpeg; q=0.6,
      image/*; q=0.5, */*; q=0.1`<br>
      但没有明确的规定如何解决两难问题。(如上例，服务器有英语的HTML页面和德语的GIF图像。)

    - 用户代理驱动模式\:
      <br>服务器通知用户代理它可用的表示法及各个表示法的元数据，用户代理将请求重新提交到选定的一种表示法的特定网址。
      <br>在上者中服务器给出两种相应\:`300 Multiple Choices`或`406 Not
      Acceptable`（当服务器驱动时，用户代理提供了接受标准但服务器无法自动选择时）。

  - 标准响应头
    >| 协议头字段       | 说明                                                                       | `示例`                                          | 是否常用 |
    >|:-----------------|:---------------------------------------------------------------------------|:-----------------------------------------------|:--------|
    >| Allow            | 服务器支持请求方法                                                          |                                                | 常设     |
    >| Content-Encoding | 文档的编码（Encode）方法。                                                  |                                                | 常设     |
    >| Content-Length   | 以八位字节数组（8位的字节）表示的响应体的长度                                | `Content-Length: 348`                          | 常设     |
    >| Content-Type     | 表示后面的文档属于什么MIME类型。                                            | `Content-Type: text/html`                      | 常设     |
    >| Date             | 发送该消息的日期和时间(按照 RFC 7231 中定义的"超文本传输协议日期"格式来发送) | `Date: Tue, 15 Nov 1994 08:12:31 GMT`          | 常设     |
    >| Expires          | 文档有效期                                                                 | `Expires: Wed, 21 Oct 2015 07:28:00 GMT`       | 常设     |
    >| Last-Modified    | 文档的最后改动时间。                                                        | `Last-Modified: Wed, 21 Oct 2015 07:28:00 GMT` | 常设     |
    >| Location         | 将页面重新定向至的地址。                                                    | `Location: /index.html`                        | 常设     |
    >| Refresh          | 表示浏览器应该在多少时间之后刷新文档，以秒计。                               |                                                | 常设     |
    >| Server           | 服务器名字。                                                               |                                                | 常设     |
    >| Set-Cookie       | 设置和页面关联的Cookie。                                                    |                                                | 常设     |