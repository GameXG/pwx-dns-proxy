**希望有兴趣的亲能够参与到这个项目中，E-mail 至 airyai@gmail.com。谢谢~**

## 2011/8/9 版本 0.1 Alpha 2： ##

  1. 修改了程序启动代码，不需要通过 twistd 运行。
  1. 优化代码：UpstreamResolver, LocalResolver。
> > UpstreamResolver 对 TCP 连接建立持久连接池，根据 config 文件的指定，在 timeout 之前 TCP 连接可以被复用。
  1. 调整配置文件，只依赖一个 config 文件。hosts 可以在 config 文件中指定，也可以由 config 文件载入外部 hosts 文件。
  1. config 文件在不同平台上通过不同策略确定目录：
  1. 增加控制台的日志输出。
  1. 修正 hosts 文件格式，以符合操作系统的 hosts 表。
  1. 修正 domain.py: lookup 函数，以修复一些域名映射的小问题。

### Linux 用户： ###

  1. 请安装 Python 2.7，以及 [Twisted-11.0](http://twistedmatrix.com/)。
  1. 请通过 git 下载源代码。运行 run.sh 即可打开代理服务器。

### Windows 用户： ###

  1. 下载 [dnsproxy-0.1-alpha-2.rar](http://pwx-dns-proxy.googlecode.com/files/dnsproxy-0.1-alpha-2.rar)，解压到任意文件夹。
  1. dnsproxy.exe 是主程序。下载之后，请修改 data/dnsproxy.conf：
> > 将 add\_server("isp", "202.96.209.133", 53, False) 里面的 202.96.209.133 修改成你的 ISP DNS。


---


This DNS Proxy Server is based on Python and Twisted Framework, and it supports almost all DNS request types including A-type and AAAA-type (IPv6).

这个 DNS 代理服务器是基于 Python 以及 Twisted 框架写成的，并且它支持几乎所有的 DNS 请求类型，包括 A 地址以及 AAAA 地址（IPv6）。

DNS responses are cached, according to their TTL.

远程服务器的 DNS 应答根据它们的 TTL 值将会被缓存在本地。

Furthermore, more than one upstream servers can be configured to use, and each request will be forwarded to one particular server of them, according to the domain name requested.

另外，这个服务器能够链接多个上游服务器，并且根据查询域名的不同，使用特定的服务器查询。

TCP connection with upstream DNS server is also available, so it can avoid most DNS pollutions.

在查询上游服务器的时候，可以使用 TCP 协议，而不是 UDP 协议。这样，就可以避免大部分 DNS 污染了。

HOSTS table is also available, supporting addresses of IPv4 and IPv6.

提供了本地 HOSTS 表的功能，支持 IPv4 和 IPv6 的地址。

The project is originally aimed to provide an all-round DNS solution for people in China mainland, in that it can be used to get correct IP addresses of GFW blocked websites. Besides, when people in mainland China use VPN service to tunnel through GFW, they can enjoy the cached abroad DNS services, as well as the ISP awared CDN services of Chinese major sites.

这个项目的初衷是为中国大陆的用户提供一个完整的 DNS 代理解决方案——因为它能够透过 GFW，获得被屏蔽的网站的真实 IP 地址。另外，当中国大陆的用户使用 VPN 翻墙的时候，他们既能够使用更安全的、国外的 DNS 服务器，也能够享受更快的上网速度——DNS 查询结果会被缓存，而且大陆拥有 CDN 的门户网站也能够通过 ISP 的 DNS 服务器查询地址，不至于翻山越岭到美国的服务器上访问这些门户网站的内容。