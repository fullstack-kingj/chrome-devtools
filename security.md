# 了解安全问题

HTTPS 为您的网站和将个人信息委托给您的网站的人提供了[重要的安全性和数据完整性](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/why-https)。在 Chrome DevTools 中使用 Security 面板调试安全问题，确保您已在自己的网站上恰当地实现 HTTPS。

### 摘要:

- 使用 Security Overview 可以立即查看当前页面是否安全。
- 检查各个源以查看连接和证书详情（安全源）或找出具体哪些请求未受保护（非安全源）。

## 安全概述

要查看页面的整体安全性，请打开 DevTools，然后转至 Security 面板。

您首先会看到 Security Overview。Security Overview 会一目了然地告诉您页面是否安全。 安全页面会通过消息 `This page is secure (valid HTTPS).` 指示

![](images/overview-secure.png)

点击 View certificate 查看[主源](https://en.wikipedia.org/wiki/Same-origin_policy)的服务器证书。

![](images/view-certificate.png)

非安全页面会通过消息 `This page is not secure.` 指示

Security 面板可以区分两种非安全页面。 如果请求的页面通过 HTTP 提供，则主源会被标记为不安全。

![](images/overview-non-secure.png)

如果请求的页面通过 HTTPS 检索，但页面会继续使用 HTTP 检索其他源的内容，然后页面仍然会被标记为不安全。这称为[混合内容](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content)页面。 混合内容页面仅受部分保护，因为 HTTP 内容可以被嗅探器获取到且易受到中间人攻击。

![](images/overview-mixed.png)

点击 View request in Network Panel 打开 Network 面板的过滤视图，然后查看具体是哪些请求通过 HTTP 提供。 这将显示来自所有源的所有未受保护的请求。

## 检查源

使用左侧面板可以检查各个安全或非安全源。

点击安全源查看该源的连接和证书详情。

![](images/origin-detail-secure.png)

如果您点击非安全源，Security 面板会提供 Network 面板过滤视图的链接。

![](images/origin-detail-non-secure.png)

点击链接可以查看具体是源的哪些请求通过 HTTP 提供。

![](images/network-one.png)

> 本文翻译自: [https://developers.google.com/web/tools/chrome-devtools/security](https://developers.google.com/web/tools/chrome-devtools/security)