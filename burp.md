<h2>Burp Suite</h2>
web提纲的视频中讲到 burp和firefox一起使用
<h3>设置代理</h3>
[ CSDN博主「Wαff1ε」<br>
原文链接：https://blog.csdn.net/Waffle666/article/details/111083913 ]<br>

burp suite代理工具是以拦截代理的方式，拦截所有通过代理的网络流量，如客户端的请求数据、服务端的返回信息等。burp suite主要拦截HTTP和HTTPS 写协议的流量，通过拦截，burp以中间人的方式对客户端的请求数据、服务端的返回信息做各种处理，以达到安全测试的目的。
在日常工作中，最常用的web客户端就是web浏览器，我们可以通过设置代理信息，拦截web浏览器的流量，并对经过burp代理的流量数据进行处理。burp运行之后，Burp Proxy默认本地代理端口为8080。**<br>Proxy（代理）<br>**

Burp Proxy的拦截功能主要由intercept（intercept拦截/截夺）选项卡中的Forward、Drop、Interception is on/off和Action构成，他们的功能如下所示。<br>

1. Forward（放包）表示将拦截的数据表或修改后的数据包发送至服务器端。<br>
2. Drop（废包）表示丢弃当前拦截的数据包<br>
3. Interception is on（拦截请求）表示开启拦截功能，单击后变为interception is off（拦截禁用），表示关闭拦截功能<br>
4. 单击Action（行动）按钮，可以将数据包进一步发送到Spider、scanner、Repeater、Intruder等功能组件做进一步测试，同时也包含改变数据包请求方式及其body的编码功能。（发送到其他功能组件）<br>

打开浏览器，输入需要访问的URL并按回车键，这时将看到数据流量经过Burp Proxy并暂停，直到单击Foreword按钮，才会继续传输下去。如果单击了Drop按钮，这次通过的数据当Burp Suite拦截的客户端和服务器交互之后，我们可以在Burp Suite的消息分析选项中查看这次请求的实体内容、消息头、请求参数等信息。**<br>Burp有四种消息类型显示数据包：Raw、Params、Headers和Hex。**

1. Raw主要显示web请求的raw格式，以纯文本的形式显示数据包，包含请求地址、Http协议版本、主机头、浏览器信息、Accept可接受的内容类型、字符集、编码方式、cookie等，可以通过手动修改这些信息，对服务器端进行渗透测试。（Raw就是以文本的形式显示数据包）
2. Params主要显示客户端请求的参数信息，包括GET或者POST请求的参数、cookie参数。可以通过修改这些请求参数完成对服务器端的渗透测试。
3. Headers中显示的是数据包中的头信息，以名称、值的形式显示数据包。
4. Hex对应的是Raw中信息的二进制内容，可以通过Hex编辑器对请求的内容进行修改，在进行00截断时非常好用。<br>

**target**
filter过滤

**Spider**
Spider的蜘蛛爬行功能可以帮助我们了解系统的机构，其中Spider爬取到的内容将在Target中展示

**Decoder**
Decoder的功能比较简单，它是Burp中自带的编码解码及散列转换的工具，能对原始数据进行各种编码格式和散列的转换。

**Repeater**
可以重复的发一个包

API就是写插件用的东西

在repeater里面的数据都可以相互转发的

**Extender（插件扩展/扩展程序）**
BApp Store是官方插件，需要专业版才可以install

**Intruder（暴力破解）**
将刚刚repeater的内容发送到intruder